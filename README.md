# game_development
Game development is the process of creating a game from concept to launch. It involves a multidisciplinary approach, combining art, design, programming, sound design, and project management to create an engaging and immersive experience for players.
#include <SDL2/SDL.h>

int main(int argc, char* argv[]) {
  // Initialize SDL
  SDL_Init(SDL_INIT_VIDEO);

  // Create a window
  SDL_Window* window = SDL_CreateWindow("Game Window", 100, 100, 640, 480, SDL_WINDOW_SHOWN);

  // Create a renderer
  SDL_Renderer* renderer = SDL_CreateRenderer(window, -1, SDL_RENDERER_ACCELERATED);

  // Game loop
  int running = 1;
  SDL_Event event;
  while (running) {
    while (SDL_PollEvent(&event)) {
      if (event.type == SDL_QUIT) {
        running = 0;
      }
    }

    // Clear the screen
    SDL_SetRenderDrawColor(renderer, 255, 255, 255, 255);
    SDL_RenderClear(renderer);

    // Draw a rectangle
    SDL_Rect rect = { 100, 100, 200, 200 };
    SDL_SetRenderDrawColor(renderer, 255, 0, 0, 255);
    SDL_RenderFillRect(renderer, &rect);

    // Update the screen
    SDL_RenderPresent(renderer);

    // Delay to control frame rate
    SDL_Delay(16);
  }

  // Clean up
  SDL_DestroyRenderer(renderer);
  SDL_DestroyWindow(window);
  SDL_Quit();

  return 0;
}
