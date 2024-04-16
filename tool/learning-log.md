# Tool Learning Log

## Tool: **kaboom.js**

## Project: **flappy bird like game**

I believe that the best way to go about creating this game is to set goals which need to be reached these goals should all come together to create a flappy bird like game, but without just copying someone elses code.
Under each goal I will have a set of subgoals, and under the subgoals I will have the code I used to achieve them as proof of my progress

Create a game like flappy bird but change it up enough to be unique:
    create a health system
       -take damage
       -potentially heal damage
       -die instantly from going offscreen but take damage from obstacles
       -if health reaches 0, die
            health(3)
            go("lose", score)
            mordecai.onCollide("pipe", () => [
		    mordecai.hurt(1)
		    addKaboom(mordecai.pos)
	        ])
The problems here came from issues with the sprite, and the effects. I got the damage part to work but once I took damage the game would crash so I had to add a place to go once you died, the lose screen. I then tried to change the sprite but due to size issues he would instantly because his body is offscreen and when you go offscreen, you die, fixed with scale(). afterward when i tried adding in additional hits they wouldn't work I would die immediatly, this was fixed by changing the health value of my sprite.
    Change the sprite
       - find a sprite suitable for use
       - implement it into the game
            sprite("mordecai")
            body(),
		    scale(0.06)
Changing the sprite was far more annoying than I thought it would be, the first issue was from it just not working and breaking the game, this was fixed by simply changing all instances of "bean" to "mordecai" The second issue was that he wouldnt fit on the screen, this was solved by using scale.
    Create obstacles
       - create "pipes"
       - randomize positions of pipes
       - continously create randomized pipes untill death
            const h1 = rand(PIPE_MIN, height() - PIPE_MIN - PIPE_OPEN)
		    const h2 = height() - h1 - PIPE_OPEN
            rect(64, h2)
            outline(4)
			area()
			move(LEFT, SPEED)
			offscreen({ destroy: true })
    Color customization
       - alter the colors of the background
       - change the colors of the pipes
       - Make one of these two dynamic (changing colors constantly)
            color(mordecai.pos.y, 0, 150)
            color(0, mordecai.pos.y, 150)
            (the above two are both for the pipes)
            setBackground(0,0,0);


### X/X/XX:
* Text

### X/X/XX:
* Text


<!--
* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->
