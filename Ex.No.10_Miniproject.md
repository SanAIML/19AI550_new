# Ex.No: 10  Implementation of 2D/3D game collection of coins
### DATE:                                                                            
### REGISTER NUMBER : 
### AIM: 
To develop a coin collection 2Din Unity 
### Algorithm:
```
Step 1: Initialize the Game
Create a 2D Unity project.
Add a Player object with Rigidbody2D and BoxCollider2D.
Add a Ground object with BoxCollider2D.
Create Coin objects and place them in the scene.
Step 2: Player Movement
Read horizontal input from the keyboard.
Move the player left or right based on the input.
Detect the Space key press.
Apply an upward force to make the player jump.
Step 3: Coin Collection
Detect collision between the player and a coin.
Increase the score by 1.
Remove the collected coin from the scene.
Step 4: Score Management
Maintain a score variable.
Update the score whenever a coin is collected.
Display the score in the console.
Step 5: Win Condition
Continuously check the score.
If the score reaches 10, display a "YOU WIN!" message.
Step 6: Enemy Interaction
Detect collision between the player and the enemy.
Display a "GAME OVER" message when a collision occurs.
```  
### Program:
```
using UnityEngine;

public class PlayerMovement : MonoBehaviour
{
    public float speed = 5f;
    public float jumpForce = 8f;

    private Rigidbody2D rb;

    void Start()
    {
        rb = GetComponent<Rigidbody2D>();
    }

    void Update()
    {
        float move = Input.GetAxis("Horizontal");

        rb.linearVelocity = new Vector2(move * speed, rb.linearVelocity.y);

        if (Input.GetKeyDown(KeyCode.Space))
        {
            rb.AddForce(Vector2.up * jumpForce, ForceMode2D.Impulse);
        }
    }
}


using UnityEngine;

public class Coin : MonoBehaviour
{
    private void OnTriggerEnter2D(Collider2D other)
    {
        if(other.CompareTag("Player"))
        {
            GameManager.AddScore();
            Destroy(gameObject);
        }
    }
}

using UnityEngine;

public class GameManager : MonoBehaviour
{
    public static int score = 0;

    public static void AddScore()
    {
        score++;
        Debug.Log("Score: " + score);
    }
}

using UnityEngine;

public class WinGame : MonoBehaviour
{
    void Update()
    {
        if(GameManager.score >= 10)
        {
            Debug.Log("YOU WIN!");
        }
    }
}


```
### Output:
<img width="956" height="545" alt="image" src="https://github.com/user-attachments/assets/560680e5-fe47-4fe4-9099-dfac68ece933" />

### Result:
Thus the game was developed using Unity and adopted AI technology.
