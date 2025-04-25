using UnityEngine;

public class PlayerMovement : MonoBehaviour
{
    public float moveSpeed = 5f;                      // Movement speed of the character
    private Vector2 movement;                         // Stores input movement direction
    private Rigidbody2D rb;                           // Rigidbody2D component

    void Start()
    {
        rb = GetComponent<Rigidbody2D>();             // Get the Rigidbody2D component
    }

    void Update()
    {
        // Get input (WASD / Arrow keys)
        movement.x = Input.GetAxisRaw("Horizontal");  // A/D or Left/Right
        movement.y = Input.GetAxisRaw("Vertical");    // W/S or Up/Down

        movement = movement.normalized;               // Normalize to prevent faster diagonal speed
    }

    void FixedUpdate()
    {
        // Apply movement using Vector2
        rb.MovePosition(rb.position + movement * moveSpeed * Time.fixedDeltaTime);
    }
}

