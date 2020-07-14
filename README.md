# Religadores_AR

Códigos religadores AR 

#Toshiba_TB_R1000_AR

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class RAYCASTARTB : MonoBehaviour
{

    string nome;
    public Animator door;
    public Animator fecho;
    public Animator corrente;
    public Animator articulacao;
    public Animator portaInterna;
    public Animator cabos;
    private bool isAnimating = false;
    private bool isAnimatingInterno = false;
    public GameObject botgiro1;
    private float speed = 0.5f;
    private Vector2 start, end;
    private Vector2 startpos, direction;
    public GameObject eixo;
    public AudioSource somporta1;
    public AudioSource somclick;
    public AudioSource somporta2;
    public Animator alav;
    private bool up = false;
    private bool down = false;
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
                case "FECHO":

                    if (Input.touchCount == 1 && Input.touches[0].phase == TouchPhase.Began)
                    {
                        if (isAnimating == false)
                        {
                            door.SetBool("aberto", true);
                            fecho.SetBool("aberto", true);
                            corrente.SetBool("aberto", true);
                            articulacao.SetBool("aberto", true);
                            isAnimating = true;
                            somporta1.Play();
                        }
                        else if (isAnimating == true & isAnimatingInterno == false)
                        {
                            door.SetBool("aberto", false);
                            fecho.SetBool("aberto", false);
                            corrente.SetBool("aberto", false);
                            articulacao.SetBool("aberto", false);
                            isAnimating = false;
                            somporta1.Play();
                        }
                    }
                    break;
                case "PUXADORINTERN0":

                    if (Input.touchCount == 1 && Input.touches[0].phase == TouchPhase.Began)
                    {
                        if (isAnimatingInterno == false)
                        {
                            portaInterna.SetBool("aberto", true);
                            cabos.SetBool("aberto", true);
                            isAnimatingInterno = true;
                            somporta2.Play();
                        }
                        else if (isAnimatingInterno == true)
                        {
                            portaInterna.SetBool("aberto", false);
                            cabos.SetBool("aberto", false);
                            isAnimatingInterno = false;
                            somporta2.Play();
                        }
                    }
                    break;

               

                case "eixo":

                    if (botgiro1.transform.rotation.eulerAngles.z < 100)
                    {
                        botgiro1.transform.Rotate(Vector3.forward * speed);
                    }
                    else { }

                    if (botgiro1.transform.rotation.eulerAngles.z > 350)
                    {
                        botgiro1.transform.Rotate(Vector3.back * speed);
                    }
                    else { }

                    

                    if (Input.touchCount > 0 && Input.GetTouch(0).phase == TouchPhase.Began)
                    {
                       
                        startpos = Input.GetTouch(0).position;

                    }

                    if (Input.GetTouch(0).phase == TouchPhase.Moved)
                    {
                        direction = Input.GetTouch(0).position - startpos;

                        if (direction.y > startpos.y)
                        {
                          
                            

                            if (botgiro1.transform.rotation.eulerAngles.z > 100 && botgiro1.transform.rotation.eulerAngles.z < 350)
                            {
                                
                                botgiro1.transform.Rotate(Vector3.forward * speed);
                                somclick.Play();
                            }
                        }

                        else
                        {

                            if (direction.y < startpos.y)
                            {
                                if (botgiro1.transform.rotation.eulerAngles.z > 100 && botgiro1.transform.rotation.eulerAngles.z < 350)
                                {
                                    
                                    botgiro1.transform.Rotate(Vector3.back * speed);
                                    somclick.Play();
                                }
                            }
                        }
                    }
                    break;

                case "ALAVANCA1":

                    if(Input.touchCount > 0 && Input.GetTouch(0).phase == TouchPhase.Began)
                    {
                        start = Input.GetTouch(0).position;
                    }
                    if (Input.touchCount > 0 && Input.GetTouch(0).phase == TouchPhase.Ended)
                    {
                        end = Input.GetTouch(0).position;

                        if(end.y > start.y && up == false && down == false)
                        {
                            alav.Play("ALAVUP");
                            up = true;
                            somclick.Play();

                        }
                        if(start.y > end.y && up == false && down == false)
                        {
                            alav.Play("ALAVDOWN");
                            down = true;
                            somclick.Play();
                        }
                        if (start.y > end.y && up == true && down == false)
                        {
                            alav.Play("ALAVUP 0");
                            up = false;
                            somclick.Play();
                        }
                        if (end.y > start.y && up == false && down == true)
                        {
                            alav.Play("ALAVDOWN 0");
                            down = false;
                            somclick.Play();

                        }
                        

                    }
                    break;
            }

        }
    }
}