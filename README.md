# Loop Trainer

A browser-based tool for rehearsing interview answers under real time pressure. Pick a question, answer it on a 90-second clock, and get feedback on both how you said it and what you said. No install, no backend, runs as a single HTML file.

## What it does

- **90-second headline timer.** A ring counts your headline window, flips to an amber checkpoint cue at 0:90, then counts your overtime in red so an overrun is impossible to miss.
- **Live delivery tracking.** Counts filler words and verbal tics ("right?", "kind of", and similar) as you speak, plus word count and words per minute.
- **Answer-only grading.** Optional AI review judges your answer on its own merits: structure, specificity, whether you actually answered the question, and where you overclaim or hedge your own work. There is no model answer to match.
- **Story bank fact-check.** Import your own notes and the grader cross-checks your claims against your record instead of scoring blind.
- **Drill mode.** You give an opening answer, the tool generates the interviewer's next question from what you actually said, and keeps drilling. This mirrors how real interviews go deep on one story.
- **Session summary.** After a loop or drill, it surfaces your recurring patterns across answers.

## Modes

- **Single** runs one question, one rep.
- **Drill one story** takes an opening answer and follows up based on it, depth of your choosing.
- **Loop** runs a few questions in a row for breadth.

## Setup

1. Open the page.
2. Open Settings. Paste your Anthropic API key (optional, only needed for content grading), pick a model, and optionally paste or upload your story bank.
3. Choose a mode, a question source, and whether to speak or type. Start.

Everything you enter is stored only in your browser. Your API key is sent only to Anthropic.

## What needs a key, and what does not

The timer, tic detection, delivery feedback, and session summary all run locally and need no key.

The content review (score, structure, honesty flags, cut and add notes, and the drill follow-up question) calls Claude and requires your own Anthropic API key. Without a key, that panel is simply off and everything else still works. Note that drill mode needs the key, since follow-ups are generated from your answer.

## Notes

- Voice input uses the browser's built-in speech recognition, which works best in Chrome. The tool falls back to typing if voice is unavailable.
- The "right?" counter is approximate, because speech transcripts drop punctuation. Read it as a directional signal.
- API usage incurs normal Anthropic API cost per graded answer. The fast, low-cost model option is good for heavy drilling.

## Tech

Plain HTML, CSS, and JavaScript in a single file. The Web Speech API for voice. The Anthropic Messages API for grading, called directly from the browser with a bring-your-own-key pattern.

---

Built by Amit Porwal.
