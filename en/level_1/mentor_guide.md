# 👨‍👩‍👧‍👦 Mentor Guide - Level 1

## 🎯 Level Overview

### Ages and Characteristics

**Target audience:** Children aged 8-9

**Cognitive characteristics at this age:**
- Concrete thinking (not abstract yet)
- Sustained attention of 20-30 minutes
- Learn best with direct manipulation
- Motivated by immediate visual results
- Need frequent celebration and positive reinforcement

**Previous experience:**
- ❌ No programming knowledge assumed
- ✅ Only need to know how to read and use mouse/keyboard basics

---

## 🎓 Pedagogical Objectives

### Main Objective

> **Awaken interest and curiosity in programming through visual and interactive experiences, establishing a positive relationship with technology and computational thinking.**

### Specific Objectives

**📚 Knowledge:**
- Basic concept of "program" as sequence of instructions
- Functions as "recipes" the computer follows
- Variables as "boxes" that store information
- Lists as collections of things

**🛠️ Skills:**
- Write simple instructions in Elixir
- Execute code in Livebook
- Identify simple errors (visually)
- Experiment by changing values

**❤️ Attitudes:**
- Curiosity to experiment
- Absence of fear of error
- Pride in own creations
- Desire to share achievements

---

## 📅 Class Planning

### Class 1: Introduction to Programming

**🎯 Objective:** Familiarization with Livebook and first code contact.

**🔑 Key Concepts:**
- What a program is
- How to "talk" with the computer
- Execute code by pressing a button

**💡 Tips:**
- Let them explore Livebook's interface briefly
- Don't explain everything at once, guide step by step
- Celebrate the first "Hello, world!" a lot
- If there's technical frustration, take breaks

**🎯 Activities:**
1. Livebook exploration (5 min)
2. First program: show text (15 min)
3. Change the message (15 min)
4. Show numbers and simple operations (15 min)
5. Challenge: personalized message (10 min)

**⚠️ Common Problems:**
- Forgetting quotes in strings → Show difference visually
- Not knowing how to execute → Point to "play" button
- Typos → Normal at this age, patience

### Class 2: Basic Functions

**🎯 Objective:** Understand functions as "tricks" we teach the computer.

**🔑 Key Concepts:**
- Function = named set of instructions
- Parameters = information we give it
- Result = what the function returns

**💡 Tips:**
- Use analogies: "Like a cooking recipe"
- "We teach the computer a new trick"
- Start with parameter-less functions
- Then add simple parameters

**🎯 Activities:**
1. Use existing functions (10 min)
2. Create first simple function (15 min)
3. Functions with parameters (15 min)
4. Combine functions (10 min)
5. Creative challenge (10 min)

**⚠️ Common Problems:**
- Confusion between defining and calling → Use "teach" vs "ask" analogy
- Forgetting `do`...`end` → Highlight visually
- Not understanding parameters → Very concrete examples

### Class 3: Colors and Sounds

**🎯 Objective:** Create attractive visual and audio outputs.

**🔑 Key Concepts:**
- Kino for interactivity
- Colors in hexadecimal (simplified)
- Basic sound effects

**💡 Tips:**
- This class is very fun! Let them experiment a lot
- Prepare examples of colors they like
- If sound isn't available, focus on visual
- Animals making sounds are a hit

**🎯 Activities:**
1. Show basic colors (10 min)
2. Create rainbow (15 min)
3. Change background colors (10 min)
4. Sound effects (15 min)
5. Project: color traffic light (10 min)

**⚠️ Common Problems:**
- Colors don't appear → Check Kino syntax
- Sounds don't work → Have visual backup
- Want to explore indefinitely → It's okay, give them time

### Class 4: Variables and Messages

**🎯 Objective:** Store information in variables and reuse it.

**🔑 Key Concepts:**
- Variable = named box that stores something
- Assignment with `=`
- String interpolation

**💡 Tips:**
- "Labeled box" analogy
- "We give names to things"
- Use meaningful names from the start
- Examples with their names, ages, favorites

**🎯 Activities:**
1. Store numbers in variables (10 min)
2. Store text (10 min)
3. Use variables in messages (15 min)
4. Operations with variables (15 min)
5. Personal presentation card (10 min)

**⚠️ Common Problems:**
- Confusing `=` with mathematical equality → "It's like putting in the box"
- Forgetting `#{}` in interpolation → Show difference
- Typing variable names → Copy/paste at first

### Class 5: Mini Quiz Game

**🎯 Objective:** Create interactivity with user inputs.

**🔑 Key Concepts:**
- Kino.Input to receive data
- Read values with Kino.Input.read
- Basic comparisons

**💡 Tips:**
- Very motivating! They're creating their first "game"
- Start with silly/fun examples
- Allow them to personalize questions
- Celebrate creativity over "correctness"

**🎯 Activities:**
1. Create text input (10 min)
2. Read and show response (10 min)
3. Simple guessing game (15 min)
4. Multiple questions (15 min)
5. Personalize their own game (10 min)

**⚠️ Common Problems:**
- Not waiting for input to execute → Explain cell order
- Reading before showing input → Cell order important
- Frustration if it doesn't work → Debug together

### Class 6: Lists and Visual Patterns

**🎯 Objective:** Work with collections of elements.

**🔑 Key Concepts:**
- List = ordered collection
- Access elements by position
- Create visual patterns

**💡 Tips:**
- Use concrete examples: list of toys, friends, colors
- Visual: show lists of colors
- Don't go deep into complex syntax
- Enum.map can wait, use direct examples

**🎯 Activities:**
1. Create lists of things (10 min)
2. Access elements (10 min)
3. Color list → visual pattern (15 min)
4. Create sequences (15 min)
5. Own design (10 min)

**⚠️ Common Problems:**
- Indices (start at 0) → Can confuse, use Enum.at
- Bracket syntax → Show clearly
- Wanting infinite lists → Limit quantity

### Class 7: Interactive Story

**🎯 Objective:** Create narrative with user decisions.

**🔑 Key Concepts:**
- Basic conditional flow (simplified if/else)
- Story concatenation
- Inputs as decisions

**💡 Tips:**
- VERY CREATIVE! Give them narrative freedom
- Can be silly or fantastic stories
- Don't focus on syntax, but on creativity
- Help them structure ideas

**🎯 Activities:**
1. Simple linear story (10 min)
2. Add inputs for name (10 min)
3. One decision → two endings (15 min)
4. Multiple paths (15 min)
5. Their own story (10 min)

**⚠️ Common Problems:**
- Too complex stories → Help simplify
- Getting lost in narrative → Focus on code
- Wanting many options → Start simple

### Class 8: Drawing with Code

**🎯 Objective:** Create visual representations with characters.

**🔑 Key Concepts:**
- Basic ASCII art
- Character repetition
- Patterns with String.duplicate

**💡 Tips:**
- Very visual and satisfying!
- Start with simple shapes (lines, squares)
- They can draw whatever they want
- Doesn't need to be perfect art

**🎯 Activities:**
1. Draw lines (10 min)
2. Create squares and rectangles (10 min)
3. Simple triangles (10 min)
4. Combine shapes (15 min)
5. Free creation (15 min)

**⚠️ Common Problems:**
- Inconsistent spacing → Normal, part of learning
- Frustration with complex shapes → Simplify
- Wanting colors → Combine with class 3

### Class 9: Review and Challenge

**🎯 Objective:** Consolidate knowledge with fun challenges.

**🔑 Key Concepts:**
- All previous combined
- Practical application
- Collaborative debugging

**💡 Tips:**
- Review main concepts briefly
- Progressive challenges, not all at once
- Work in pairs if possible
- Celebrate different approaches

**🎯 Activities:**
1. Quick interactive quiz (10 min)
2. Challenge 1: Variables and colors (10 min)
3. Challenge 2: List of favorites (10 min)
4. Challenge 3: Mini story (15 min)
5. Share creations (15 min)

**⚠️ Common Problems:**
- Mental block → Guide with questions, not answers
- Comparing with others → Emphasize everyone at own pace
- Wanting it perfect → "Done is better than perfect"

### Class 10: Final Visual Project

**🎯 Objective:** Create personal project integrating everything learned.

**🔑 Key Concepts:**
- Application of all concepts
- Simple planning
- Execution and testing

**💡 Tips:**
- Let them choose something that excites them
- Help so it's not too ambitious
- It's okay not to finish everything
- Process is more important than result
- CELEBRATE EVERYTHING!

**🎯 Project Ideas:**
- Interactive birthday card
- Question game about themselves
- Adventure story
- ASCII art gallery
- Age calculator and messages
- Compliment generator

**🎯 Class Structure:**
1. Planning: what I want to do (10 min)
2. Start programming (30 min)
3. Test and adjust (10 min)
4. Decorate/improve (10 min)
5. Present (if they want) or save

**⚠️ Common Problems:**
- Too ambitious project → Help divide into phases
- Perfectionism → Remember can continue later
- Comparison → Each project is unique

---

## 🗣️ Language and Communication

### Appropriate Vocabulary

At this age, use everyday language:

| ❌ Avoid | ✅ Use instead |
|----------|----------------|
| "Define a function" | "Teach it a new trick" |
| "Parameters" | "The information it needs" |
| "Return a value" | "What it tells us back" |
| "String" | "Text" or "words" |
| "Integer" | "Whole number" |
| "Execute" | "Make it work" or "press play" |

### Guiding Questions

Instead of giving answers, ask:

**🔸 To explore:**
- "What do you think this line of code does?"
- "Why do you think that happened?"
- "Can you find where it says your name?"

**🔸 For debugging:**
- "What did you expect to happen?"
- "What happened instead?"
- "Do you notice anything different in this line?"

**🔸 For reflection:**
- "What did you enjoy most?"
- "What was hardest?"
- "If you could change something, what would it be?"

---

## 🎨 Methodology

### Learning Cycle per Class

1. **🎯 Clear objective** (2 min)
   - "Today we're going to teach the computer colors"
   
2. **👀 Demonstration** (5-8 min)
   - Show a working example
   - Do it yourself first, step by step
   
3. **🛠️ Guided practice** (15-20 min)
   - They do the same as they saw
   - Support them when needed
   
4. **🎨 Experimentation** (15-20 min)
   - Change values, colors, texts
   - Personalize the exercise
   
5. **🏆 Challenge** (10-15 min)
   - Something new combining what they learned
   - Optional but motivating
   
6. **📝 Closure** (3-5 min)
   - "What did we learn today?"
   - Celebration of achievements

### Pedagogical Principles

**✨ See to believe:**
- First show the final result
- Then explain how to get there
- Children need to know "what for?"

**✨ Touch and modify:**
- Let them write code as soon as possible
- Modify existing code before creating from scratch
- Copy-paste is okay at first

**✨ Error as learning:**
- "How interesting! What does the message say?"
- "Let's be code detectives"
- Never: "It's wrong" → Always: "Let's see what happened"

**✨ Frequent celebration:**
- "Look what you achieved!"
- "That was really creative"
- "Wow, how did you think of that?"

---

## 🚧 Managing Challenges

### Frustration

**Signs:**
- Negative language: "I can't", "It's too hard"
- Wanting to give up
- Irritability

**Strategies:**
1. Active break (5 min stretch/play)
2. Go back to something simpler that works
3. Divide problem into smaller parts
4. Do that specific step together
5. Change activity and come back later

### Boredom

**Signs:**
- Finishes very quickly
- Distracted, not paying attention
- "I already know this"

**Strategies:**
1. Extra challenges more complex
2. Extreme personalization of exercise
3. Help another classmate (if group)
4. Free exploration of Livebook
5. Skip some basic exercises

### Creative Block

**Signs:**
- Doesn't know what to do in free project
- "I can't think of anything"
- Copies examples exactly

**Strategies:**
1. **Triggering questions:**
   - "What's your favorite [animal/color/superhero]?"
   - "What would you like the computer to say?"
2. **Limited options:**
   - "Do you prefer to make A, B, or C?"
3. **Start together:**
   - First lines with you, then alone
4. **Inspiration:**
   - Show examples from other kids (without comparing)

---

## 📊 Evaluation

### Formative Evaluation (Continuous)

Don't evaluate with grades, observe:

**✅ Actively participates**
- Tries exercises
- Asks questions
- Experiments without fear

**✅ Understands basic concepts**
- Can explain in their words what code does
- Identifies simple errors
- Modifies code intentionally

**✅ Shows positive attitude**
- Enjoys classes
- Wants to share creations
- Doesn't give up at errors

### Warning Signs

⚠️ **Requires more support:**
- Constant frustration
- Doesn't enjoy any activity
- Compares negatively with others
- Can't write any functional code

**Action:**
- More time on basic concepts
- Shorter sessions
- 1-on-1 focus instead of group
- Review if difficulty level is appropriate

✅ **Ready to advance:**
- Completes exercises easily
- Asks for more challenges
- Creates projects on own initiative
- Explains concepts to others

**Action:**
- Add complex extensions
- Introduce level 2 concepts
- Skip basic classes if very evident

---

## 🎁 Additional Resources for Mentors

### Learn Alongside Them

If you don't know Elixir, learn together!

**Resources:**
- [Elixir School](https://elixirschool.com/) - Multiple languages
- [Exercism.org](https://exercism.org/tracks/elixir) - With mentors
- [Official documentation](https://elixir-lang.org/getting-started/introduction.html)

### Complementary Activities (Without computer)

**🎲 Everyday algorithms:**
- Write "recipe" for making a sandwich
- Give instructions to get to a place
- Discover "bugs" in wrong instructions

**🎨 ASCII art on paper:**
- Create designs with characters
- Geometric patterns
- Before programming them

**🎭 Human programming:**
- One child gives instructions, another executes literally
- Teaches precision and debugging

### Recommended Reading

- **"Hello Ruby" series** - Linda Liukas
  - Illustrated books about programming for children
  - Very visual and narrative

- **"My First Coding Book"** - Various authors
  - Basic illustrated concepts

### Educator Communities

- **Elixir Forum - Education Category**
  - Share experiences
  - Ask for advice
  
- **Code.org - Educational resources**
  - Although not Elixir, good pedagogical practices

---

## ✅ Mentor Checklist

### Before each class:

- [ ] Reviewed today's notebook
- [ ] Tested that everything works
- [ ] Identified potential difficult points
- [ ] Prepared extra examples if needed
- [ ] Have good energy and patience

### During class:

- [ ] Started with enthusiasm
- [ ] Left time to experiment
- [ ] Asked questions instead of giving answers
- [ ] Celebrated achievements (big and small)
- [ ] Handled errors with positivity

### After class:

- [ ] Celebrated what was learned
- [ ] Child is proud of something they did
- [ ] Saved their work
- [ ] Anticipated next class with excitement

---

## 💪 Encouragement, Mentor

Remember:

> "You're not teaching programming. You're awakening curiosity, building confidence, and showing they can create amazing things. Code is just the tool."

**You can do it. They can do it. Together you'll create magic! ✨🚀**

---

## 📞 Next Step

Once you're clear on this guide, review each class individually before giving it. Each notebook has specific notes and suggestions.

**Forward, mentor! 🎓**

