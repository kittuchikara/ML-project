1) Mixed Emotional Signals
Text:
The forest session made me calmer, but part of me still feels uneasy. Part of me wants rest, part of me wants action.

True Label: mixed
Predicted: overwhelmed
Reason:

The sentence contains both positive and negative emotional signals.
The TF-IDF model struggles to interpret mixed sentiment sentences.

2) Subtle Overwhelm
Text:

The mountain session gave me a pause, but the pressure is still sitting hard on me. I'm carrying too much in my head.

True Label: overwhelmed
Predicted: mixed
Reason:

The model may interpret “pause” as a calming signal, even though the overall emotional state indicates overwhelm.

3) emantic Meaning Missed

Text:

"i feel mentally clear after the mountain session"

True Label: focused
Predicted: restless

Reason:
The phrase “mentally clear” implies focus, but TF-IDF cannot capture semantic meaning well.

4) Conflicting Words

Text:

The mountain session made me calmer, but part of me still feels uneasy. Part of me wants rest, part of me wants action.

True Label: mixed
Predicted: restless

Reason:
Words like “calmer” and “but” create contradictory signals.

5) Hidden Stress Signals

Text:

The cafe session wasn't enough today; everything still feels heavy and too much. It's hard to know where to begin.

True Label: overwhelmed
Predicted: mixed

Reason:
The emotional stress is implied rather than explicitly stated.

6) Physical vs Emotional Exhaustion

Text:

even after the forest track, i feel exhausted and emotionally overloaded i feel emotionally tired i almost wanted to stop midway

True Label: overwhelmed
Predicted: calm

Reason:
The model may interpret exhaustion as physical fatigue instead of emotional overwhelm.

7) Similar Vocabulary Across Classes

Text:

Even after the mountain track, I feel exhausted and emotionally overloaded. I feel emotionally tired.

True Label: overwhelmed
Predicted: mixed

Reason:
Words like “exhausted” appear across multiple emotional states.

8) Emotional Transition

Text:

I started scattered, but the cafe session helped me lock in on what matters. My to-do list feels less chaotic.

True Label: focused
Predicted: restless

Reason:
The sentence describes a transition from distraction to focus, which TF-IDF models struggle to capture.

9) Indirect Emotional Description

Text:

The cafe ambience helped me breathe slower and let go of some pressure.

True Label: calm
Predicted: neutral

Reason:
The emotion is described indirectly through physiological change.

10) Ambiguous Positive Reflection

Text:

I wasn't expecting much, but the rain session made me feel quiet inside My shoulders feel less tense

True Label: calm
Predicted: restless

Reason:
The emotional tone is subtle and depends on context beyond individual words.