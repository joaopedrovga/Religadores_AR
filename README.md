# Religadores_AR

Códigos religadores AR 

#ABB_PCD_2000_AR

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class RAYCASTARABB : MonoBehaviour
{
    string nome;
    
    public Animator   door;
    public Animator fecho;
    public Animator corrente;
    private bool isAnimating = false;
    public GameObject led1;
    public GameObject led2;
    public GameObject led3;
    public GameObject led4;
    public GameObject led5;
    public GameObject led6;
    public GameObject led7;
    public GameObject onled1;
    public GameObject onled2;
    public GameObject onled3;
    public GameObject onled4;
    public GameObject onled5;
    public GameObject onled6;
    public GameObject onled7;
    private bool bla = false;
    private bool bla1 = false;
    private bool bla2 = false;
    private bool bla3 = false;
    private bool bla4 = false;
    private bool bla5 = false;
    private bool bla6 = false;
    // Start is called before the first frame update
    void Start()
    {

    }
   
    // Update is called once per frame
    void Update()
    {

        

            Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);
            RaycastHit Hit;
            if (Physics.Raycast(ray, out Hit))
            {
                nome = Hit.transform.name;
                switch (nome)
                {                

                    case "FECHO":

                    if (Input.touchCount == 1 && Input.touches[0].phase == TouchPhase.Began)
                    {
                        if (isAnimating == false)
                        {
                            door.SetBool("aberto", true);
                            fecho.SetBool("aberto", true);
                            corrente.SetBool("aberto", true);
                            isAnimating = true;
                        }
                        else if (isAnimating == true)
                        {
                            door.SetBool("aberto", false);
                            fecho.SetBool("aberto", false);
                            corrente.SetBool("aberto", false);
                            isAnimating = false;
                        }
                    }
                        break;

                    case "BOT1":

                    if (Input.touchCount == 1 && Input.touches[0].phase == TouchPhase.Began)
                    {
                            if(bla == false)
                            {
                                led1.SetActive(false);
                                onled1.SetActive(true);
                                bla = true;
                            }
                            else
                            {
                                if(bla == true)
                                {
                                    led1.SetActive(true);
                                    onled1.SetActive(false);
                                    bla = false;
                                }
                            }
                        }
                        break;

                    case "BOT2":

                    if (Input.touchCount == 1 && Input.touches[0].phase == TouchPhase.Began)
                    {
                            if (bla1 == false)
                            {
                                led2.SetActive(false);
                                onled2.SetActive(true);
                                bla1 = true;
                            }
                            else
                            {
                                if (bla1 == true)
                                {
                                    led2.SetActive(true);
                                    onled2.SetActive(false);
                                    bla1 = false;
                                }
                            }
                        }
                        break;

                    case "BOT3":

                    if (Input.touchCount == 1 && Input.touches[0].phase == TouchPhase.Began)
                    {
                            if (bla2 == false)
                            {
                                led3.SetActive(false);
                                onled3.SetActive(true);
                                bla2 = true;
                            }
                            else
                            {
                                if (bla2 == true)
                                {
                                    led3.SetActive(true);
                                    onled3.SetActive(false);
                                    bla2 = false;
                                }
                            }
                        }
                        break;

                    case "BOT4":

                    if (Input.touchCount == 1 && Input.touches[0].phase == TouchPhase.Began)
                    {
                            if (bla3 == false)
                            {
                                led4.SetActive(false);
                                onled4.SetActive(true);
                                bla3 = true;
                            }
                            else
                            {
                                if (bla3 == true)
                                {
                                    led4.SetActive(true);
                                    onled4.SetActive(false);
                                    bla3 = false;
                                }
                            }
                        }
                        break;

                    case "BOT5":

                    if (Input.touchCount == 1 && Input.touches[0].phase == TouchPhase.Began)
                    {
                            if (bla4 == false)
                            {
                                led5.SetActive(false);
                                onled5.SetActive(true);
                                bla4 = true;
                            }
                            else
                            {
                                if (bla4 == true)
                                {
                                    led5.SetActive(true);
                                    onled5.SetActive(false);
                                    bla4 = false;
                                }
                            }
                        }
                        break;

                    case "BOT6":

                    if (Input.touchCount == 1 && Input.touches[0].phase == TouchPhase.Began)
                    {
                            if (bla5 == false)
                            {
                                led6.SetActive(false);
                                onled6.SetActive(true);
                                bla5 = true;
                            }
                            else
                            {
                                if (bla5 == true)
                                {
                                    led6.SetActive(true);
                                    onled6.SetActive(false);
                                    bla5 = false;
                                }
                            }
                        }
                        break;

                    case "BOT7":

                    if (Input.touchCount == 1 && Input.touches[0].phase == TouchPhase.Began)
                    {
                            if (bla6 == false)
                            {
                                led7.SetActive(false);
                                onled7.SetActive(true);
                                bla6 = true;
                            }
                            else
                            {
                                if (bla6 == true)
                                {
                                    led7.SetActive(true);
                                    onled7.SetActive(false);
                                    bla6 = false;
                                }
                            }
                        }
                        break;
                }
            }


        
    }
}
