# OSINT Challenge Write-Up: Tracking the Submarine

## Challenge Overview

- **Challenge Name:** Tracking the Submarine
- **Category:** OSINT (Open-Source Intelligence)
- **Points:** [Insert Points Value]
- **Difficulty:** [Insert Difficulty Level]
- **Description:**

> We have been tracking a highly suspicious submarine believed to be harboring many enemy skiddies. Unfortunately, this satellite image is rather out of date. Your mission is to locate the submarines using a more up-to-date image, and tell us what class they are with their NATO reporting name — a letter from the NATO phonetic alphabet, spelled out.  
> We want to know precisely where the aft end of the northernmost submarine attached to the pier is. Communicate its location in three words. Include the NATO reporting name of the class of submarine in your answer.  
> Submission format: `PCTF{three.position.words.class_name}`  
> Example submission: `PCTF{employing.broken.imports.sierra}`

---

## Initial Approach: Understanding the Task

The challenge description provided us with an outdated satellite image, likely of a submarine base. Our objective was clear but multifaceted: 

1. **Locate a more recent image** of the base to track the submarines using open-source tools.
2. **Identify the class of the northernmost submarine** using its NATO reporting name (spelled as a letter from the phonetic alphabet).
3. **Pinpoint the exact aft end of the northernmost submarine** using What3Words, a geolocation tool that breaks locations into three-word addresses.

With this roadmap in hand, the challenge promised not just a test of research skills, but also precision and accuracy.

---

## Step 1: Leveraging Google Reverse Image Search

The first task involved locating a more up-to-date image of the submarine base. I began by uploading the provided satellite image to Google’s reverse image search feature. After sorting through several results, one specific match stood out: an image hosted on a Blogger website.

- **Website URL:**  
  [https://buscando-desde-el-cielo.blogspot.com/2011/11/la-mitica-base-de-poliarny.html](https://buscando-desde-el-cielo.blogspot.com/2011/11/la-mitica-base-de-poliarny.html)

Upon visiting the website, I was greeted by a blog post titled **"La mítica base de Polyarny,"** or *"The legendary Polyarny Military Base."* This confirmed our suspicion that the Polyarny base, a known Russian submarine hub, was indeed the location of interest.

---

## Step 2: Investigating Polyarny Submarine Base

With confirmation of the base's identity, the next challenge was to find a more up-to-date satellite image. I used various mapping tools, beginning with **Google Maps** and moving on to **Bing Maps** for different perspectives.

At this stage, it became clear that more than just the general location was needed—we required precise coordinates to satisfy the challenge's requirements. This is where **What3Words** came into play.

---

## Step 3: Using What3Words for Precision Location

What3Words is a fascinating geolocation tool that breaks the entire globe into 3-meter squares, assigning each square a unique combination of three words. Armed with this tool, I switched to **satellite view** and zoomed in on the Polyarny Submarine Base.

After scanning the area, I was able to pinpoint the **aft end** of the **northernmost submarine docked at the pier**. By focusing on the exact position of the aft, What3Words generated the following three-word address:

- **Location:** `bagels.light.vivid`

Thus, the first part of the flag was uncovered:  
`PCTF{bagels.light.vivid.`

---

## Step 4: Identifying the Submarine Class

Now that the precise location was determined, the final task was to identify the class of submarine docked at the Polyarny Base. The challenge required us to submit the NATO reporting name, which corresponds to the class of the submarine, as part of the final flag.

To accomplish this, I first measured the length of the submarine using the mapping tools' ruler feature. The measurement came to approximately **200 feet**—a crucial detail in narrowing down the list of possible submarine classes.

### Cross-Referencing with NATO Submarine Classes

Armed with the length and location, I began cross-referencing the characteristics of known submarine classes. Although the Sierra-class was one potential candidate (as mentioned in the challenge example), after further research, the length and shape more closely matched the **Kilo-class submarine**.

Thus, I concluded that the submarine in question was indeed a **Kilo-class**.

---

## Conclusion: Assembling the Final Flag

With all the pieces of the puzzle now in place, the final flag was assembled as:

```plaintext
PCTF{bagels.light.vivid.kilo}

---

This challenge was a perfect example of how multiple open-source intelligence tools can be combined to achieve precision, from satellite image searches to geolocation tools like What3Words and submarine class identification. It demonstrated the value of methodical research, attention to detail, and cross-referencing diverse sources.

## Key Takeaways:

- **Research Efficiency:** Google reverse image search and What3Words were instrumental in narrowing down the exact location of the submarine.
- **Technical Precision:** Measurement tools were vital in identifying the submarine’s class.
- **Cross-Verification:** Using multiple mapping platforms like Google and Bing helped verify the location and characteristics of the submarines.
