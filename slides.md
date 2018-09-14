# The Most Annoying Website
## (aka Power of the Web Platform)

---

# Feross Aboukhadijeh

Slides: https://speakerdeck.com/feross/the-annoying-site-aka-power-of-the-web-platform-v2

---

## What was this talk about?
- In the past, the web was "the wild west" (90s)
- Over time, browsers/the web became more secure and less fun (00s)
- Now, browsers are becoming more powerful and expose certain APIs (10s - Present)
- As a demonstration, Feross created https://theannoyingsite.com/

---

## Why do this?
- To waste spammers' time
- To send to your coworkers in #digital-developers and see who bites

---

## Examples of what you can do
- Creating new windows
```
const newWin = window.open('', '', 'width=100, height=100')
```
- Moving the window
```
newWin.moveTo(100,100)
```
- Resizing the window
```
newWin.resizeTo(500,500)
```
- Requesting webcam
```
navigator.mediaDevices.getUserMedia({video: true})
```
- etc

---

## Personal Favorites
- `window.speechSynthesis`
```
window.speechSynthesis.speak(
    new window.SpeechSynthesisUtterance("I'm sorry Dave, I'm afraid I can't do that")
);
```
- Safari Picture in Picture (example on theannoyingsite.com)

- Changing cursor image
```
body {
    cursor: url(http://rs916.pbsrc.com/albums/ad9/sugarycandy/cursors/glitter.gif~c100), auto;
}
```

---


## 4 Tiers of Permission
- Always works
- Always works, but requires https
- User interaction required
- User permission required

---

## Demo Time!
All examples found at https://github.com/feross/TheAnnoyingSite.com

---

# The Loader is a Lie

---

## Bernie Cheng
## Gordana Jekic Dzunic

GeoTab, telematics company that needs to load and visualize millions of data points

---

<div id="loader"></div>
<style>
    #loader {
        border-color: lightblue;
        border-top: steelblue;
        border-radius: 50%;
        border-width: 5px;
        border-style: solid;
        height: 50px;
        width: 50px;
        margin: 0 auto;
        animation-name: spin;
        animation-duration: 1s;
        animation-iteration-count: infinite;
        animation-timing-function: linear;

    }

    @keyframes spin {
        0% {
            transform: rotate(0deg);
        }

        100% {
            transform: rotate(360deg);
        }
    }
</style>

## Potential Problems

- No sign of progress
- Perception of longer loading time
- What comes next is a surprise

---

## Suggestions
- Use loaders in moderation
    - Short operations that only last a few seconds
- It's better to at least indicate to the user that there is some progress being made
    - Progress bars
    - Percentages
    - Time remaining

---

## (Their) Demo
- Loading a bar chart with traffic data over a period of several months
- Used an infinite loading spinner waiting for a single request
- Conference wifi was being super flaky, which actually seemed to really help their point about loading spinners
    - We were totally unsure of when the bar chart would load

---

## Improvements they made in future iterations
- Breaking out fetching data into multiple requests and render data once a request finishes
- Progress bar that displayed the percentage of data that rendered along with and which months had finished rendering

---

## Their last demo
- Rendering a map with a million data points over multiple requests
- Still allowed the map to be usable while data was still coming in shown via progress bar
- Improved the user experience, since users were able to interact with the map and there was the progress bar to show them when more data comes in
