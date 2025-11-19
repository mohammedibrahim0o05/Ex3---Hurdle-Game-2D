# Ex3---Hurdle-Game-2D

## AIM:

To develop a 2D game using C# program in unity .

## ALGORITHM:

STEP 1:Create a 2D project in unity.

STEP 2:Add player,hurdles,coins,track in the frame and add the valid collider2D component.

STEP 3:Click Assets->Create-># Script.

STEP 4:create player.cs and coinmanger script and add c# code.

STEP 5:Click canvas->Gamemanager->add Score and value.

STEP 6:Drag the script to player and coin.

STEP 7:Run the scene and display the output.

## PROGRAM:

Developed by: M.CHANDRU

Register no: 212222230026

### player.cs:
```python
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using System.Threading;

public class player : MonoBehaviour
{
    public float speed;
    public float jumpforce;
    private Rigidbody2D rb;
    public CoinManager cc;
    void Start()
    {
        rb = GetComponent<Rigidbody2D>();
    }

    // Update is called once per frame
    void Update()
    {
        float moveinp = Input.GetAxisRaw("Horizontal");
        transform.position += new Vector3(moveinp, 0, 0) * speed * Time.deltaTime;

        if (Input.GetKeyDown(KeyCode.Space) && Mathf.Abs(rb.velocity.y) < 0.001f)
        {
            rb.AddForce(new Vector2(0, jumpforce), ForceMode2D.Impulse);
        }
    }
    private void OnTriggerEnter2D(Collider2D collision)
    {
        if (collision.CompareTag("Destroy"))
        {
            cc.coincount++;
            Destroy(collision.gameObject);
        }
    }
}
```

### Coin Manager:
```python
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class CoinManager : MonoBehaviour
{
    public int coincount;
    public Text value;
    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        value.text = coincount.ToString(); 
    }
}
```
## OUTPUT:

![Screenshot (159)](https://github.com/chandrumathiyazhagan/Ex3---Hurdle-Game-2D/assets/119393023/d59377fa-a064-45ae-b33f-77805c3913ec)

![Screenshot (160)](https://github.com/chandrumathiyazhagan/Ex3---Hurdle-Game-2D/assets/119393023/1a826de4-176e-4bd3-85a9-db45934d2d43)

## RESULT:

Thus a 2D game using C# program in unity is developed successfully.
