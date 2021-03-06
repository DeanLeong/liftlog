# LiftLog

# Project Overview

## Project Name

LiftLog
https://deanleongliftlog.netlify.app/

## Project Description

The idea of this website is to give the user the ability to keep track of their weightlifting workouts. At it's most basic it will act as a virtual notebook. The idea is that the user will be able to submit the following:
The "Day" the literal date and/or "Day" of a program they are following.
The lift: user-provided text input becuase everyone does things differently. Ex, "Bench Press".
Reps: How many reps of the exercise they are doing. Ex 5\*5 etc.
Notes: A text input for misc notes.
On the homepage the user can see the basics of their most recently created submissions such as Day and Lift, and the on click it will expand to show more detail.

## Wireframes

https://imgur.com/a/yF7uOXF

## Component Hierarchy

![](https://i.imgur.com/WHMkfnF.png)

## API and Data Sample

https://airtable.com/tbluhjztK95AS1HEe/viwY9qxc21uDKTFVo?blocks=hide

![](https://i.imgur.com/bDI4VZs.png)

### MVP/PostMVP

#### MVP

MVP:
1 - A homepage including the submission form and a navbar to the other pages. -Done

2 - A "Saved Workouts" page of the previously submitted workouts. -Done

3 - Navbar to other pages - availible on all pages. - Done

4 - A lg to kg calculator page. -Done

#### PostMVP

Post MVP:

1 - More detailed submission forms, for example, the ability to add more exercises under the same day.

2 - Search through saved workouts? - Attempting - Didn't get working in time but this is something that would be great to come back to.

3 - More detail on the homepage. - Done.

## Project Schedule

| Day        | Deliverable                                        | Status     |
| ---------- | -------------------------------------------------- | ---------- |
| October 8  | Prompt / Wireframes / Priority Matrix / Timeframes | Complete   |
| October 9  | Project Approval                                   | Complete   |
| October 10 | Core Application Structure (HTML, CSS, etc.)       | Complete   |
| October 10 | Pseudocode / actual code                           | Complete   |
| October 11 | Working Homepage                                   | Complete   |
| October 12 | Working Saved Workout page and Calc page           | Complete   |
| October 13 | Styling                                            | Complete   |
| October 14 | MVP                                                | Complete   |
| October 15 | Post MVP                                           | Complete   |
| October 16 | Presentation                                       | Complete |

## Timeframes

| Component             | Priority | Estimated Time | Time Invested | Actual Time |
| --------------------- | :------: | :------------: | :-----------: | :---------: |
| Working with API      |    H     |      5hrs      |      2.5      |     2.5     |
| Homepage              |    H     |     10hrs      |       2       |      2      |
| Submit Form           |    H     |     10hrs      |       8       |      8      |
| Saved Page            |    H     |     15hrs      |     12.5      |    12.5     |
| Calculator Page       |    l     |      3hrs      |       3       |      3      |
| Render Saved Workouts |    H     |     10hrs      |       2       |      2      |
| CSS Styling           |    l     |     10hrs      |      18       |     18      |
| Total                 |    H     |     50hrs      |     48hrs     |    48hrs    |

Priortiry Matrix:
![](https://i.imgur.com/COaiIzy.png)

General Notes on Plan:
1 - Set up Basics of the "Home Page" This includes the header, NavBar and the submission form.

2 - Get the submission form working. Since the content of the "Show page" is going to be user-generated the submission form must be functional.

3 - Get the show page working. This means that the data submitted on the home page should render on the show page.

4 - Get the lb to kg calculator page working.

5 - CSS styling. Basic styling will be done as I go, the overall styling will be done after the JS/React is done.

## SWOT Analysis

### Strengths:

I have a strong sense for planning and the ability to get started on a project.

### Weaknesses:

I frequently hit walls when coding.

### Opportunities:

I have the opportunity to look back at lessons and exercises to help me get the project complete.

### Threats:

I'm not the strongest coder, so a threat is getting stuck and not knowing what to do.

### Code Snippet:

```
function SubmitWorkout() {
  const [day, setDay] = useState("")
  const [exercise, setExercise] = useState("")
  const [weight, setWeight] = useState("")
  const [reps, setReps] = useState("")
  const [notes, setNotes] = useState("")

  const handleSubmit = async (e) => {
    e.preventDefault()

    const fields = {
      day,
      exercise,
      weight,
      reps,
      notes,
    }
    const airtableURL = `https://api.airtable.com/v0/${process.env.REACT_APP_AIRTABLE_BASE}/liftlog`

    await axios.post(
      airtableURL,
      { fields },
      {
        headers: {
          Authorization: `Bearer ${process.env.REACT_APP_AIRTABLE_KEY}`
        }
      }
    )
    setDay("")
    setExercise("")
    setWeight("")
    setReps("")
    setNotes("")
  }

  return (
    <div className="submit-page">
      <h2>Submit A Workout</h2>
    <div className="submit-workout">
    <form onSubmit={handleSubmit} className="submit-form">
      <label className="form-label" htmlFor="Day">Day:</label>
        <input className="form-input"
          name="Day"
          type="text"
          placeholder="Day"
          value={day}
          onChange={(e) => setDay(e.target.value)}
        />
```

I'm pretty proud of my submission code because this is something I distinctly remember struggling with earlier in the unit. I planned on taking a good amount of time getting this to work but I was able to do it relatively quicky. Even though the code is simple, this is definitely not something that I would have been able to do just a few weeks ago, nevermind writing, styling and getting it fully functional in just a few hours. This feeling applies to the project overall. I was definitely struggling with React through the two weeks learning it, but when I sat down to start my project everything came together and left me feeling confident in taking on a more complex project in the future.
