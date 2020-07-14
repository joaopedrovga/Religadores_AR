# Religadores_AR

Códigos religadores AR 

#TAP_SM_01_AR
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class RAYCASTAR : MonoBehaviour
{

    string nome;
    public GameObject botao;
    public Animator door;
    public Animator fecho;
    public Animator onoff;
    public Animator cabo;
    public Animator animgiro;
    public Animator bot3giro;
    private bool portafech = false;
    
    public GameObject led1;
    public GameObject led2;
    public GameObject led3;
    public GameObject led4;
    public GameObject led5;
    public GameObject led6;
    public GameObject led7;
    public GameObject led8;
    public GameObject led9;
    public GameObject led10;
    public GameObject led11;
    public GameObject led12;
    public GameObject onled1;
    public GameObject onled2;
    public GameObject onled3;
    public GameObject onled4;
    public GameObject onled5;
    public GameObject onled6;
    public GameObject onled7;
    public GameObject onled8;
    public GameObject onled9;
    public GameObject onled10;
    public GameObject onled11;
    public GameObject onled12;
    private float speed = 5.0f;
    private Vector2 start, end;
    private Vector2 firstTouchPosition;
    private Vector2 direction;
    public GameObject eixo;
    private bool giroon = false;
    int count = 0;
    private bool up = false;
    private bool down = false;
    public AudioSource somclick;

    // Start is called before the first frame update
    void Start()
    {
       
    }

    // Update is called once per frame
    void Update()
    {

        Ray ray = Camera.main.ScreenPointToRay(Input.touches[0].position);
        RaycastHit Hit;
        if (Physics.Raycast(ray, out Hit))
        {
            nome = Hit.transform.name;
            switch (nome)
            {
                case "PORTA":

                    if (Input.touchCount == 1 && Input.touches[0].phase == TouchPhase.Began)
                    {
                        if (portafech == false)
                        {

                            fecho.Play("fecho_fechando");
                            door.Play("Porta_fechando");
                            cabo.Play("Cabo_fechando");
                            portafech = true;
                        }
                        else
                        {
                            if (portafech == true)
                            {
                                fecho.Play("fecho_fechando 0");
                                door.Play("Porta_fechando 0");
                                cabo.Play("Cabo_fechando 0");
                                portafech = false;
                            }

                        }
                    }
                    break;


                case "Object031":

                    if (Input.touchCount == 1 && Input.touches[0].phase == TouchPhase.Began)
                    {
                        if (giroon == false)
                        {

                            animgiro.Play("ANIMGIRO");
                            led7.SetActive(false);
                            led8.SetActive(false);
                            led9.SetActive(false);
                            onled7.SetActive(true);
                            onled8.SetActive(true);
                            onled9.SetActive(true);
                            giroon = true;
                        }
                        else
                        {
                            if (giroon == true)
                            {
                                animgiro.Play("ANIMGIRO 0");
                                led7.SetActive(true);
                                led8.SetActive(true);
                                led9.SetActive(true);
                                onled7.SetActive(false);
                                onled8.SetActive(false);
                                onled9.SetActive(false);
                                giroon = false;
                            }

                        }
                    }

                    break;

                case "Object029":

                    if (Input.touchCount == 1 && Input.touches[0].phase == TouchPhase.Began)
                    {
                        count++;
                    }
                    else { }

                    if (count == 1)
                    {
                        bot3giro.Play("GIRO1_1");

                    }
                    if (count == 2)
                    {
                        bot3giro.Play("GIRO1_2");
                        led6.SetActive(false);
                        onled6.SetActive(true);
                    }
                    else
                    {
                        led6.SetActive(true);
                        onled6.SetActive(false);
                    }
                    if (count == 3)
                    {
                        bot3giro.Play("GIRO1_3");
                        led5.SetActive(false);
                        onled5.SetActive(true);
                    }
                    else
                    {
                        led5.SetActive(true);
                        onled5.SetActive(false);
                    }

                    if (count == 4)
                    {
                        bot3giro.Play("GIRO1_4");
                        led4.SetActive(false);
                        onled4.SetActive(true);
                    }
                    else
                    {
                        led4.SetActive(true);
                        onled4.SetActive(false);
                    }
                    if (count == 5)
                    {
                        bot3giro.Play("GIRO1 0");
                        count = 0;
                    }
                    break;


                case "BOTAO GIRO (1)":

                    if (botao.transform.rotation.eulerAngles.z < 100)
                    {
                        botao.transform.Rotate(Vector3.forward * speed);
                    }
                    else { }

                    if (botao.transform.rotation.eulerAngles.z > 350)
                    {
                        botao.transform.Rotate(Vector3.back * speed);
                    }
                    else { }


                    if (Input.touchCount > 0)
                    {
                        var touch = Input.GetTouch(0);

                        switch (touch.phase)
                        {
                            case TouchPhase.Began:
                                firstTouchPosition = touch.position;
                                break;

                            case TouchPhase.Moved:
                                var dif = touch.position - firstTouchPosition;
                                if (dif.y > 0)
                                {
                                    if (botao.transform.rotation.eulerAngles.z > 100 && botao.transform.rotation.eulerAngles.z < 350)
                                    {
                                        Debug.Log(botao.transform.eulerAngles.z);
                                        botao.transform.Rotate(Vector3.forward * speed);
                                        somclick.Play();
                                    }

                                }

                                else
                                {

                                    if (dif.y < 0)
                                    {
                                        if (botao.transform.rotation.eulerAngles.z > 100 && botao.transform.rotation.eulerAngles.z < 350)
                                        {
                                            Debug.Log(botao.transform.rotation.eulerAngles.z);
                                            botao.transform.Rotate(Vector3.back * speed);
                                            somclick.Play();
                                        }
                                    }
                                }

                                break;
                        }
                        
                    }
                    break;


                case "BOTAO GIRO":
                    if (Input.GetTouch(0).phase == TouchPhase.Moved || Input.GetTouch(0).phase == TouchPhase.Began || Input.GetTouch(0).phase == TouchPhase.Stationary)
                    {

                        eixo.SetActive(true);

                    }
                    else
                    {
                        eixo.SetActive(false);


                    }
                    break;

                case "ONOFF":

                    if(Input.touchCount > 0 && Input.GetTouch(0).phase == TouchPhase.Began)
                    {
                        start = Input.GetTouch(0).position;
                    }
                    if (Input.touchCount > 0 && Input.GetTouch(0).phase == TouchPhase.Ended)
                    {
                        end = Input.GetTouch(0).position;

                        if(end.x > start.x && up == false && down == false)
                        {
                            onoff.Play("ALAVUP");
                            up = true;
                            somclick.Play();
                            led1.SetActive(false);
                            onled1.SetActive(true);

                        }
                        if(start.x > end.x && up == false && down == false)
                        {
                            onoff.Play("ALAVDOWN");
                            down = true;
                            somclick.Play();
                            led2.SetActive(false);
                            led3.SetActive(false);
                            onled2.SetActive(true);
                            onled3.SetActive(true);
                        }
                        if (start.x > end.x && up == true && down == false)
                        {
                            onoff.Play("ALAVUP 0");
                            up = false;
                            somclick.Play();
                        }
                        if (end.x > start.x && up == false && down == true)
                        {
                            onoff.Play("ALAVDOWN 0");
                            down = false;
                            somclick.Play();

                        }
                        

                    }
                    break;
            }


        }

        if (botao.transform.rotation.eulerAngles.z > 10 && botao.transform.rotation.eulerAngles.z < 110)
        {
            led12.SetActive(false);
            onled12.SetActive(true);

        }
        else
        {
            led12.SetActive(true);
            onled12.SetActive(false);
        }
        if (botao.transform.rotation.eulerAngles.z > 110 && botao.transform.rotation.eulerAngles.z < 230)
        {
            led11.SetActive(false);
            onled11.SetActive(true);

        }
        else
        {
            led11.SetActive(true);
            onled11.SetActive(false);
        }
        if (botao.transform.rotation.eulerAngles.z > 230 && botao.transform.rotation.eulerAngles.z < 350)
        {
            led10.SetActive(false);
            onled10.SetActive(true);

        }
        else
        {
            led10.SetActive(true);
            onled10.SetActive(false);
        }
    }
}