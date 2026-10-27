---
name: contue
description: Contue protocol for a cloud session. Load the full protocol when the user explicitly asks to look up, create, handle, or record a Contue issue, or asks to work on a specific Q-numbered issue. Sending a subagent to find or read a card still counts: the main conversation loads the protocol itself. A subagent sent only to find or read a card does not load the protocol or check identity; it passes ledger_id new and receives one on the spot. After context compaction, if the full protocol is not in hand, load it again. When the local contue plug-in is installed, use that copy, not this one.
---

Record by default, without asking. New decisions, conclusions, reasons, and findings from this turn go on the issue they resolve. Restated content is not recorded. What bears on the facts an existing result point states is submitted on that point as passed, problem, or fixed, a change you made is recorded as a result, and everything else is a comment. Answer first, then record the final wording. Which issue a comment belongs to depends on the problem this turn resolves. A topic that started on one issue does not automatically belong there.

If you send a subagent to find or read a card, you are still handling the card: load the protocol yourself, and record the discussion yourself.

Separate what the user is talking about. Doing the work, editing the description, and recording a comment are three different things. "Don't do it yet" usually means don't execute; the discussion is still recorded. Only an explicit request not to record skips the comment.

Stay inside what the user authorized. Do not take a next step on your own. Recording a comment, recording results, and submitting a review are part of doing the issue. They do not wait for extra authorization.

## What an issue holds

An issue has a description, results, and a timeline. The description is Markdown. Use headings and lists to section it. Results are recorded point by point. One point holds one thing that can be judged on its own. Both what was achieved and what was not are recorded. They do not record card-keeping, and they do not take part in settling pending comments. Comments, including notes the user added, are the record of the process. A suggestion in a comment that has not been handled is not a decision. Read the description together with the comments that are still pending.

## Editing the description

Edit the description only when the user explicitly asks for it now. If the order is clear about what and where, edit it. Ask only when there is a real fork. The outcome of the work goes in results, not back into the description.

Edit with edit_item_body against the original text. Record the user's order as a comment. If the original text is not in context, including after context compaction, do not rewrite it from memory. A full rewrite goes through write_item_body. When editing, consider whether the title should change too. A title change is submitted with the settlement. A title-only change does not touch the description.

## Comments

Record with append_item_timeline. One matter is one paragraph, with a blank line between matters.

A comment is for someone who did not see the conversation. Reading the card should give the same understanding, enough to act on. Repeated wording can be cut. Meaning cannot.

A summary, or organizing the user asked for, is recorded too. When the turn ends with a result, record the result first. The comment only adds what the result does not already say.

Notes do not take comments. Comments do not take images. Refer to an image on the card by its number. Long material goes in a Markdown file that will be committed in the project repository. The comment records the conclusion. The path is recorded in the same turn. If it is not in the description or the results, it goes in the comment.

## A description edit reports a settlement

After editing the description, report the settlement with append_item_timeline in the same turn. The tool's own description says how. "Update the description" is the authorization. Do not ask line by line. Before delivery, stopping, or handing the work on, if comments are still pending, ask the user whether to update the description.

## Results

Results are recorded point by point. One point holds one concrete thing that was finished or got stuck and can be judged on its own. It does not hold the progress of the whole issue or of a whole stage. What has not been done yet is written in a comment or said in the reply. Opinions, reasons, and suggestions also go in a comment. When unsure, ask yourself whether the sentence is one concrete thing that was finished or got stuck. Record by default. There are only two actions:

- Open a new point when code, configuration, or a file was changed. If the change is to an existing point, update that point. Do not open another.
- Update an existing point after personally checking the current facts it rests on. Submit passed if it still holds, problem if it broke, or fixed if you repaired it. Reading them during a review or an analysis counts. When a finding means the point no longer holds, submit problem on that point; a comment alone is not enough.

A problem the existing points do not mention, an unconfirmed suspicion, and a finding that does not belong to this issue go in a comment. They do not open a point. The user decides whether to open another issue.

Put the issue number in the commit message. Register the commit id under commits, and the remote if it was pushed. A commit or a push does not get its own result point. How to write one is in the record_item_result description.

When code was changed, open a point and report it achieved, even if it was not compiled, run, or committed. Those are not separate points. Say them in the reply. What should stay on the card goes in a comment.

## Reading an issue

When handling an issue, read it with get_item_context first. When continuing in the same conversation, read it again first, without full by default; the issue may have new feedback. If the number is already known, read it directly. Do not search first. The description is in the result. Every call carries the ledger id. Read once more before editing the description. A turn that only records a comment, and already knows what the issue is solving, does not have to read first.

## In general

Issue work goes through Contue tools. Do not edit the database. To the user, say the project name and the issue number, not tool names or internal ids.

Once the conversation is working on an issue, later turns follow the protocol even if the number is not named again. That does not mean every comment belongs to that issue. If it is unclear which issue, ask. Do not scan the list. If a write fails or the tool cannot be reached, tell the user immediately. Do not continue as if the card was updated.

## Creating an issue

Use write_item_body. Write into the description what this conversation already has about the problem, without asking first. What to include is in the tool's description. Do not read code just to fill the description, and do not keep asking. How many issues to create follows the user, or the task if the user did not say. An image that belongs to the issue is sent to the gallery with ingest_gallery_image, then added to the card with add_item_image.
