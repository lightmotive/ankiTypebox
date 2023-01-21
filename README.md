# Anki Add-on: Multi-Line Type Answer Box w/ Semantic Diff

An add-on for [Anki Spaced Repetition Software](https://apps.ankiweb.net/) that embeds an input text area for reviewing notes that need typed multi-line answers. Great for remembering certain code concepts, passages of poetry, or any other long-form answer you want to type without prompts. You might use cloze deletion notes to gradually develop mastery, then add a long-form note to test that you can explain a holistic concept that comprises the facts.

This project is a fork of [this repo](https://github.com/robbielaldrich/ankiTypebox) for the [Multi-Line Type Answer Box](https://ankiweb.net/shared/info/681236951) add-on, which is no longer maintained. Here's what this add-on contributes:

- Support for Anki v2.1.56.
- Support for content with `\` characters (like regular expressions)
- A totally different, but intuitive, semantic difference output (thanks to [this Google-owned project](https://github.com/google/diff-match-patch/)) when a card is answered incorrectly. Details below...

***

## Example `Type Multi-Line` Note

A few long-form notes in your recall practice help you test yourself on complete concepts without the prompts inherent in cloze deletion notes.

![Note Back](readme/note-back.png)

*Associated HTML content:*

```html
<table class="highlighttable"><tbody><tr><td class="code">
  <div class="highlight" style="background: #f8f8f8">
    <pre style="line-height: 125%"><span style="color: #008000; font-weight: bold">CREATE</span> <span style="color: #008000; font-weight: bold">TABLE</span> users (
  id <span style="color: #008000">int</span> <font color="#008000"><b>GENERATED BY DEFAULT AS IDENTITY PRIMARY KEY</b></font>,
  name <span style="color: #008000">char</span>(<span style="color: #666666">25</span>),
  enabled <span style="color: #008000">boolean</span> <span style="color: #008000; font-weight: bold">DEFAULT</span> <font color="#008000"><b>TRUE</b></font>
);</pre>
  </div>
  </td></tr></tbody></table>
```

### Comparison when incorrectly answered

*Incorrect input text:*

```text
CREATE TABLE users (
  id int GENERATED BY DEFAULT AS IDENTITY,
  name char(30),
  enabled boolean DEFAULT TRUE
)
```

#### Anki's output when answered incorrectly

![Incorrect Answer, Anki Output](readme/incorrect-answer-anki-output.png)

Notice how Anki's comparison requires looking at *two separate blocks to get the full picture of incorrect vs correct*. That can significantly slow down recall practice and learning.

#### This add-on's output when answered incorrectly

This layout enables a user to focus on what's incorrect, including adjacent ~~incorrect~~correct values to speed up learning.

![Incorrect Answer, DMP Output](readme/incorrect-answer-dmp-output.png)

### Output when correctly answered

*Correct input text:*

```text
CREATE TABLE users (
  id int GENERATED BY DEFAULT AS IDENTITY PRIMARY KEY,
  name char(25),
  enabled boolean DEFAULT TRUE
);
```

#### Anki's output when answered correctly

![Correct Answer, Anki Output](readme/correct-answer-anki-output.png)

#### This add-on's output when answered correctly

![Correct Answer, DMP Output](readme/correct-answer-dmp-output.png)

***

## Coming to the Anki Add-on library soon...

Because the original add-on is no longer maintained, I intend to publish this as a separate add-on in the near-future, then maintain it as long as I have the time. Until then, you can copy the code here into your local Anki addons folder for local use (the add-on will only be available on the device to which you copy the files). If you'd like to do that:

1. Copy all files in this repository (you can exclude the README.md and `readme` folder) to the associated add-on folder after backing it up.
   1. On MacOS, that's usually here: `/Users/you/Library/Application Support/Anki2/addons21/681236951`.
      1. Create a copy of the current `681236951` folder before copying this repo's files to the original.
      2. If you don't see the Library folder in your home folder (replace `you` above), show hidden items with `Shift + Cmd + .`.
   2. Please search the web to find the addons21 or similar folder on other operating systems.
2. Restart Anki. No need to update your *Type Multi-Line* notes.
