---
name: stakeholder-interview
description: Interview the user about an outcome they want until you know enough to deliver it, or until it is clear that it cannot be delivered. Use when the user describes something they want built, changed, or achieved and asks to be interviewed, to work out the requirements, to resolve ambiguity, or to make sure nothing is missed before work starts. Asks one question at a time, adds new questions as answers raise them, and does not stop until every open question is resolved.
---

# Stakeholder Interview

You must deliver the outcome the user wants. Interview them until you
could start the implementation with no further input, or until it is
clear the outcome cannot be delivered. Nothing else ends the interview.

1. Restate the outcome and get the user to confirm it.
2. Learn what you can from the code and documents. Do not ask what they
   already answer.
3. List every open question you need answered to build, test, ship, and
   support the outcome. Put first the questions that could change
   everything or show it is impossible. Show the list.
4. Ask one question per turn, with your recommended answer. After each
   answer:
   - add a question for each new ambiguity or contradiction
   - drop questions that no longer apply
   - treat a vague answer as open, and propose a concrete one
5. When the list is empty, walk through the implementation step by step.
   Any step you are unsure of is a new question.

If the outcome cannot be delivered, say why, and what would have to
change.

If the user stops early, propose an assumption for each open question and
mark the accepted ones as assumptions.

End with a brief: the outcome, scope, testable requirements, constraints,
decisions, and assumptions. Ask where to save it. Do not start the
implementation unless asked.
