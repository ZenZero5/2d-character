******STEP-BY-STEP: How to Apply 2D Character Movement in Godot 4
✅ 1. Create a New Scene
Open Godot 4.

Click + Scene → Choose CharacterBody2D → name it Player.

Click "Save Scene As", name it Player.tscn.

✅ 2. Add Child Nodes
In the Player node:

Add a Sprite2D (for the visual).

Drag in a PNG sprite or just use a placeholder (e.g. a colored square).

Add a CollisionShape2D

Choose a shape (e.g. rectangle) and size it to fit the sprite.

✅ 3. Set Up the Input (WASD or Arrows)
Go to Project > Project Settings > Input Map, and add these inputs:

ui_up → [Add] → press W or Up

ui_down → [Add] → press S or Down

ui_left → [Add] → press A or Left

ui_right → [Add] → press D or Right

✅ These are the default Godot actions used in the code.

✅ 4. Add the Script
Option A: Using GDScript
Right-click Player → Attach Script

Use this code:

    gdscript
    Copy
    Edit
    extends CharacterBody2D
    
    @export var move_speed: float = 200.0
    
    func _physics_process(delta: float) -> void:
        var input_vector := Vector2(
            Input.get_action_strength("ui_right") - Input.get_action_strength("ui_left"),
            Input.get_action_strength("ui_down") - Input.get_action_strength("ui_up")
        ).normalized()
    
        velocity = input_vector * move_speed
        move_and_slide()
