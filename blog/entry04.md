# Entry 4
##### 3/12/24

The game works, and as a plus its actually fun too! the main issue of the sprite being too big for the screen and dying instatly is completely gone thanks to scale(), scale() allows me to change the size of my sprite freely.

const mordecai = add([
		// sprite() means it's drawn with a sprite of name "bean" (defined above in 'loadSprite')
		sprite("mordecai"),
		// give it a position
		pos(width() / 4, 0),
		// give it a collider
		area(),
		// body component enables it to fall and jump in a gravity world
		body(),
        // change the size of the sprite
		scale(0.06),
        // give the sprite a health value(how many hits it can take before it dies)
		health(3),
	])

You might also notice that in my code I have health(3), thats right, I figured out the health system and now my guy can take three hits to any obstacle before being sent to the game over screen. I did have a new issue to deal with while I was making the health system. the issue is that it worked but you had no visual indication that you were taking damage, you would just phase through the wall twice before getting a game over on the third wall. this was quickly fixed by addKaboom() which serves as a visual marker for damage taken

mordecai.onCollide("pipe", () => [
		mordecai.hurt(1),
		addKaboom(mordecai.pos)
	])

	mordecai.on("death", () => {
    go("lose", score)
	addKaboom(mordecai.pos)
})

// check for fall death
	mordecai.onUpdate(() => {
		if (mordecai.pos.y >= height() || mordecai.pos.y <= CEILING) {
			// switch to "lose" scene
			go("lose", score)
		}
	})

this code checks for what type of damage you took, if you go above the ceiling or below the floor, its an automatic game over, doesn't matter how much health you have. If you crash into a wall, the kaboom animation plays at your location and you take one damage out of three total, if you crash 3 times, its game over.

I feel like I have made excelent progress towards my mvp, I didnt make everything all on my own but I did change a large amount of the code for it to be mostly origional, all i need now is a way to change the background and ill be golden, or at the very least gilded.

[Previous](entry03.md) | [Next](entry05.md)

[Home](../README.md)