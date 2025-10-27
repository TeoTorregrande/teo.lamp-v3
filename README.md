#include "raylib.h" // <-- asegúrate de que raylib esté correctamente instalado
#include <raylib.h>
#include <string>// para usar std::cout si lo necesitas
using namespace std

int main() {
    // Inicialización de la ventana
    const int screenWidth = 800;
    const int screenHeight = 600;
    InitWindow(screenWidth, screenHeight, "Esfera en movimiento");

    // Variables de la esfera
    Vector2 posicion = { screenWidth / 2.0f, screenHeight / 2.0f };
    Vector2 velocidad = { 250.0f, 250.0f };
    float radio = 40.0f;
    Color color = { 0, 121, 241, 255 }; // Azul vibrante
    int rebotes = 0;

    SetTargetFPS(60);

    // Bucle principal del juego
    while (!WindowShouldClose()) {
        // Movimiento
        posicion.x += velocidad.x * GetFrameTime();
        posicion.y += velocidad.y * GetFrameTime();

        // Rebotes
        if ((posicion.x + radio) >= screenWidth || (posicion.x - radio) <= 0) {
            velocidad.x *= -1;
            rebotes++;
        }
        if ((posicion.y + radio) >= screenHeight || (posicion.y - radio) <= 0) {
            velocidad.y *= -1;
            rebotes++;
        }

        // Dibujar
        BeginDrawing();
        ClearBackground(RAYWHITE);
        DrawCircleV(posicion, radio, color);
        DrawText(TextFormat("Rebotes: %i", rebotes), 10, 10, 20, DARKGRAY);
        EndDrawing();
    }
    CloseWindow(); // Cerrar ventana

    return 0;
}
    CloseWindow(); // Cerrar ventana
    return 0;
}
