A game engine can be viewed as a layered system where game-specific logic sits on top of reusable engine systems, which themselves abstract platform differences and hardware APIs. This separation allows games to be built independently of the operating system and graphics backend while maximizing code reuse.

A game engine can conceptually be seen as follows -> 

```css
┌─────────────────────────────┐
│          Game Code          │  ← rules, logic, gameplay
├─────────────────────────────┤
│        Engine Systems       │  ← reusable tech
├─────────────────────────────┤
│   Platform / Abstraction    │  ← OS + window + input
├─────────────────────────────┤
│      Graphics / Audio API   │  ← GPU, sound, hardware
└─────────────────────────────┘
```
## Layered Game Engine Architecture

### 1. Game Code
- Game-specific logic and rules
- Player behavior, AI decisions
- Game states, UI flow, level logic
- Scripts or gameplay modules

**Examples**
- Unreal Engine: C++ gameplay code, Blueprints
- Unity: C# scripts, MonoBehaviours
- Custom engines: Main loop + game state logic

---

### 2. Engine Systems
Reusable, game-agnostic systems provided by the engine.

**Typical systems**
- Rendering (scene submission, render graphs)
- Physics
- Audio
- Animation
- ECS / object model
- Asset management & streaming
- Job / task systems

**Examples**
- Unreal Engine: Renderer (Nanite, Lumen), Chaos physics, animation graph
- Unity: URP/HDRP, PhysX, animation & audio systems
- Lightweight engines: Basic renderer, input handling, texture/audio loaders

---
### 3. Platform Abstraction Layer
Hides operating system differences and provides a uniform interface.

**Responsibilities**
- Window creation
- Input (keyboard, mouse, controller)
- File system
- Timing
- Threading
- Networking

**Examples**
- Unreal Engine: Platform-specific runtime layer
- Unity: Platform backends per build target
- Custom engines: SDL, GLFW, or custom OS abstraction layer

---

### 4. Graphics / Audio APIs
Low-level hardware and driver interfaces.

**Graphics APIs**
- DirectX 12
- Vulkan
- Metal
- OpenGL

**Audio APIs**
- WASAPI
- CoreAudio
- OpenAL

**Notes**
- These APIs are not part of the engine logic itself
- Engines issue commands to these APIs to drive GPU and audio hardware
