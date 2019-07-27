# cpp opengl boilerplate



## Install opengl 3
```
brew install glfw3
brew install libsoil
```

## Refercence
https://github.com/gameprogcpp/code


## Init OpenGL
```
  // Use the core OpenGL profile
	SDL_GL_SetAttribute(SDL_GL_CONTEXT_PROFILE_MASK, SDL_GL_CONTEXT_PROFILE_CORE);
	
  // Specify version 3.3
	SDL_GL_SetAttribute(SDL_GL_CONTEXT_MAJOR_VERSION, 3);
	SDL_GL_SetAttribute(SDL_GL_CONTEXT_MINOR_VERSION, 3);
	
  // Request a color buffer with 8-bits per RGBA channel
	SDL_GL_SetAttribute(SDL_GL_RED_SIZE, 8);
	SDL_GL_SetAttribute(SDL_GL_GREEN_SIZE, 8);
	SDL_GL_SetAttribute(SDL_GL_BLUE_SIZE, 8);
	SDL_GL_SetAttribute(SDL_GL_ALPHA_SIZE, 8);
	
  // Enable double buffering
	SDL_GL_SetAttribute(SDL_GL_DOUBLEBUFFER, 1);
	
  // Force OpenGL to use hardware acceleration
	SDL_GL_SetAttribute(SDL_GL_ACCELERATED_VISUAL, 1);

  // Create OpenGL window
	mWindow = SDL_CreateWindow("OpenGL Window", 100, 100, 1024, 768, SDL_WINDOW_OPENGL);
	if (!mWindow)
	{
		SDL_Log("Failed to create window: %s", SDL_GetError());
		return false;
	}

	// Create an OpenGL context
	mContext = SDL_GL_CreateContext(mWindow);

	// Initialize GLEW
	glewExperimental = GL_TRUE;
	if (glewInit() != GLEW_OK)
	{
		SDL_Log("Failed to initialize GLEW.");
		return false;
	}

	// On some platforms, GLEW will emit a benign error code,
	// so clear it
	glGetError();


```

## Covert the drawing from SDL_Render to OpenGL
```
  void Game::GenerateOutput()
  {
    // Set the clear color to gray
    glClearColor(0.86f, 0.86f, 0.86f, 1.0f);
    // Clear the color buffer
    glClear(GL_COLOR_BUFFER_BIT);

    // TODO: Draw the scene

    // Swap the buffers, which also displays the scene
    SDL_GL_SwapWindow(mWindow);
  }
```