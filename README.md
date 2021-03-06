# mastermind_pair

This is a collaboration between [Robert Suazo](https://github.com/rsuazo) and [Michael Marchand](https://github.com/marchandmd)

We're building a Mastermind Game similar to the one found [here as part of The Odin Project curriculum](https://www.theodinproject.com/courses/ruby-programming/lessons/oop#project-2-mastermind)

## 1/6/2020:
1. created 'lib/' directory
2. moved 'mastermind_pair.rb' into `lib/`
3. initialized 'rspec'
4. updated RSpec configuration to suppress console output during testing
5. reduced `@colors` array to `%w[r o y g b i v]` since the existence of `blue` and `black` created some ambiguity
6. removed `@converted_code` since it's now redundant
7. Added new lines to the `#get_guess` method to provide more instructions to user
8. created `lib/run_this_file.rb` and moved the engine into `run_this_file.rb`
9. built out `#get_guess` validation
10. roughed in a cheap board, by adding `@board`

## 1/7/2020:
1. Added `@feedback` to provide feedback RE each turn
2. Created `spec/mastermind_pair_spec.rb`
3. Wrote failing test for `#output_progress`
4. Wrote passing test for `#output_progress`
5. Changed `#output_progress` to `#update_progress`
6. struggled mightily with the logic to provide hints, LOL
7. pushed a working version of a complete game

## 1/11/2020: 
All this is actually readily apparent in the commit history/PR request..but I'll do one more day to make my actions obvious: 
1. Created `lib/markdown_notes/`
2. added a `Board` class
3. re-factored the `Game` class to leverage the `Board` class
4. created `Board#prompt_player`

## 1/14/2020:
1. created `Game#introduction`: During every turn, the `board_object_instance#prompt_player` method would print `Guess the secret code` which is unnecessary. So I moved the text into `Game#introduction` because I feel like the introduction should happen only once...but prompting the player should happen on every turn...


2. So now, running `ruby lib/run_this_file.rb`...creates some output that looks like this: 

```
WELCOME TO MASTERMIND!

Guess the secret code

your choices are: 

(r)ed (o)range (y)ellow (g)reen (b)lue (i)ndigo (v)iolet
your choices are: 

(r)ed (o)range (y)ellow (g)reen (b)lue (i)ndigo (v)iolet
```

so now this needs to be fixed...  
3. fixed #2 by doing this: 

```ruby
round == 1 ? introduction : board_object_instance.prompt_player
```

in the `#play_round` method

4. I moved the call to `#updated_progress` from within `#get_guess` to it's own call within `#play_round`

5. I also moved the logic to display the board from within `#get_guess` to it's own call in `#play_round`...however, this would be better suited for it's own method, probably

6. `#update_progress` isn't working...so I'm going to maybe start testing it...

7. changed the name of `#update_progress` to `#gather_feedback`

8. Uncovered a massive bug with the `#gather_feedback` method.....but it's location within the `#get_guess` method isn't that big of a deal breaker. So i'm going to leave it alone. 