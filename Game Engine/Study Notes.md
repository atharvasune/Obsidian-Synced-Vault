So into game development and already hitting the first barrier. Started with install `raylib` and the first error i get is `Unable to build, because raylib not found`. Now why this happened is simple, I used it as `#include "raylib.h"` but the compiler, in this case `clang` needs to know about it. Unlike java where gradle and python where pip handle installation of dependencies there is nothing for c++, raylib is literally a binary i downloaded using `brew install raylib` . So i need to use [[Cmake]] to make this work

First code -> 
```c++
#include "raylib.h"

int main() {
	InitWindow(800, 450, "Game Engine Start");
	SetTargetFPS(60);
	while (!WindowShouldClose()) {
		BeginDrawing();
		ClearBackground(RAYWHITE);
		DrawText("Engine Started", 250, 280, 30, BLACK);
		EndDrawing();
	}
	CloseWindow();
}
```

This is just a simple example of writing a [raylib](https://www.raylib.com/) code that creates a window of size 800x450 and writes Engine Started in it. 

Quite a few learnings 

Second thing we did today 
```c++
#include "raylib.h"
#include <stdio.h>
#include <string>
#include <iostream>

int main()
{
	const int screenWidth = 1600;
	const int screenHeight = 900;
	std::string pressedKey = "NONE";
	InitWindow(screenWidth, screenHeight, "Game Engine Start");
	SetTargetFPS(60);
	while (!WindowShouldClose())
	{
		BeginDrawing();
		ClearBackground(RAYWHITE);
		int fps = GetFPS();
		DrawText(std::to_string(fps).c_str(), 10, 10, 30, BLACK);
		DrawText((pressedKey + " was pressed").c_str(), (screenWidth-8)/2, screenHeight/2, 30, BLACK);
		int keyPressed = GetKeyPressed();
		switch (keyPressed)
		{
			case KEY_UP:
				pressedKey = "UP";
				break;
			case KEY_DOWN:
				pressedKey = "DOWN";
				break;
			case KEY_LEFT:
				pressedKey = "LEFT";
				break;
			case KEY_RIGHT:
				pressedKey = "RIGHT";
				break;
			default:
				break;
		}
		EndDrawing();
	}
	CloseWindow();
}
```

So while this code is simple a lot of learnings. 
1. Every time a new frame is rendered, and if your state variables are initialized inside rendering loop then they will be overridden
2. Rendering loop should only read any inputs and set those state variables, and do rendering stuff nothing else. 
3. For any new render the window should be cleared everytime, else nothing new is rendered. 