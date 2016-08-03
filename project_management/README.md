# Project Management

What project management software is used or what buzzword describes the
systems a team claims to manage itself by are tactical answers to higher
level questions. It's more important to understand what the right
questions to ask are than what your answer is, because if you don't
understand the question, then how can you know if your answer is wrong?

I think project management boils down to consistently answering two questions.

* What do high performing teams operate like? (by extension: are we
  doing this?)
* What is the nature of the project the team is attacking?

## High Performing Teams

Asana, Flow, Basecamp, these things are attempts at providing structure
and answers to this question. Each has a thesis the software
springs from. Because, of all the project management software I've used,
I like Basecamp the most, I strongly agree with their approach:

1. Effective teams take a record of every meeting. This is super helpful if someone needs to step in and get up to speed on things quickly.
2. Productive teams don’t let questions linger. This means having chat
   somewhere.
3. Every great team has a leader who makes sure things are moving along. Which is why they created an automatic check-in to keep project managers up to date. If not using Basecamp, then define what this is. Team members don’t have to create progress reports or anything like that. It's the resonsibility of the team leader to find what they need.
4. To-do lists make it clear who is responsible for what and all the deadlines.
5. File storage makes everything available in one place, and it can act as a backup disk.
6. The central schedule keeps everyone up to date on major milestones, vacation schedules, and any other upcoming events that are important to know about. All these soft skills are even more critical with remote teams.

Thus, at the outset of any project, no matter what actual software or
such is being used, these 6 questions must be answered with a strong
consensus. (Often it will be something simple, like a slack channel for
point 2).

## Adapting to project nature

Generally, the projects we work on have two fundamental and important
aspects:

* They're products, projects that (hopefully) go on forever and thus
  have no actual set end date
* Ultimately, these projects are for others - companies, teams, people.

This has several consequences:

If a project will ideally go on forever, then the right way to make
sense of it is to cut out sensible, relatively independent chunks of
work. These interrelated scopes are the things that are actually
time-bound.

Decisions on application frameworks, ui frameworks, infrastructure, etc
must be made from the POV of the other team, and cap the downside in the
event that the Good team needs to peace out of a project.

**Scopes**: a pieces of customer value in the product that are
orthogonal to each other


## Practical Application in Ruby on Rails w/ Flow

For each scope, we must consider these areas:

* UI
* App Code
* Framework
* Infrastructure
* QA

Caveat: different scopes can have different needs. Some can be entirely
dev, some can be entirely design, some can be entirely infrastructure.

At the time of this writing the most recent project is Recruiting Board. The next project is Satchel.

We eliminate the waterfall that happens between design and development. We chunk out a specific area of customer value (like signup), actually code it all out in the UI (but not wired up with any app code). Like, the form is a `link_to` to the next page. We explore through everything like that, iterate there in the browser, and direct everything from the ui perspective before even touching app code (major mistake of how we worked on RB - Pete would do designs, I’d do coding, we’d have to large reconciliations between each other instead of constant smaller ones).

Ex - to achieve the UI level, then go deeper:

* Chris (developer) sets up the directory structure for a given scope, and possibly
  sparsely populates it.
* Pete (designer) produces a low-fi version there in the browser (no colors, no
  visual hierarchy involving css)
* These previous two points can flip flop, and its not actually
  important who does them.
* This is iterated upon until the given scope is figured and will
  provide the value for the user its supposed to.
* Views become wired up to controllers, etc.
* Concurrently, views get visual design.
* The scope is merged, deployed, and reviewed (QA)

We start at the UI level, work down into the App Code level, and then
run it through the remaining ones.

We manage the project by scopes rather than by roles, that just gets confusing. This way, we can neatly visually organize our tasks by scope, and actually have a feeling of progress rather than attacking a large, endless list. (Accomplishes the same results in a way that feels much better).

## Some Key Things

* For infrastructure needs, the client will provide payment info and one
  centralized email that all configurations will happen through. This
way, developers can go set up all the services needed for the app to
function.
* Communicate barriers. Don't know where in an app an actual file should
  go? Don't know how to get something to show up on the page? What was
that Git command? What is that concept again?
* Accountability - who is responsible for enforcing accountability? How
  should that happen? This is actually a different thing:
* When is a thing truly important vs arbitrarily urgent? This is just
  software, its just a website. Sometimes launch really does need to
happen, this thing really does need to be out, but 95% of the time
that's just not true. So accountability needs to be filtered by this
distinction: delays are okay.

## In Flow

If we aren't relying on Flow, and operating despite it, then need to
change how we're using it until we do actually rely upon it.

Flow should answer several questions:

* Manager/Project Leader/Client perspective: where is everything at? How
  far along is it all? What can I expect?
* Design/Dev perspective: How can I decide what to work on next? How do I communicate
  what I need? Where?

Such I think it makes sense to have a couple things:

* Project description answers the 6 questions with directives: Have a
  question? do 'x'. Need to upload a file? put it 'y'.
* Each 'scope' gets its own board (in the kanban view) or section (in the list view). When all the tasks in a scope are complete, delete it.
* There will need to be one scope that exists and serves as a backlog.

Backlogs are messy. They are where ideas about a project go to die and
never be looked at. So I'd like to come up with something better.

* All important dates are put on the schedule, and meetings are run
  centered around achieving certain scopes by specific dates.
* The worst thing that can happen is if we tell a client we'll have
  something done for them by a certain time, and then that time comes
around and we don't. To avoid that, we must behave as such: the schedule is a guess. 'Delays' are actually fine, except when
  they're not. Center discussion on risks, unknowns, and talk in terms
of tradeoffs.

## Final Thoughts

I'm not sure how to effectively choose scopes in a project, it shifts
from project to project, but the tendency will be to do the easy thing
first. So a good criteria is: if this scope exists largely the same in
other projects (like user authentication), then do it later. Start with
the most domain-specific areas.
