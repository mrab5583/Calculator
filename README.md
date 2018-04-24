/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package practice;

import java.util.Scanner;

/**
 *
 * @author Mr.AB
 */

public class Practice 
{
    public static void main(String[] args) 
    {
        Prac1 p=new Prac1();
        
        int count=0;
        System.out.println("Input in format : 00JAN/FEB/MAR,1999");
        System.out.println("Enter the date : ");
        Scanner s=new Scanner(System.in);
        String date1=s.nextLine();
        
        count+= Integer.parseInt(date1.substring(8,10)); // STEP 1
        
        count+=count/4; // STEP 2
        
        int date2=Integer.parseInt(date1.substring(0,2)); // STEP 3
        count+=date2;
        
        String month=date1.substring(2,5); // STEP 4
        count+=p.monthcal(month);
        
        int year=Integer.parseInt(date1.substring(6,10)); // STEP 5 
        count+=p.yearcal(year);
        
        int mod7=count%7; // FINAL STEP
        p.finalresult(mod7);
    } 
}
class Prac1 //extends Practice
{
    void finalresult(int mod7)
    {
        if(mod7==0)
            System.out.println("Its SUNDAY");
        if(mod7==1)
            System.out.println("Its MONDAY");
        if(mod7==2)
            System.out.println("Its TUESDAY");
        if(mod7==3)
            System.out.println("Its WEDNESDAY");
        if(mod7==4)
            System.out.println("Its THURSDAY");
        if(mod7==5)
            System.out.println("Its FRIDAY");
        if(mod7==6)
            System.out.println("Its SATURDAY");
    }
    int monthcal(String month)
    {
        int ret=0;
        if(month.equalsIgnoreCase("jan") || month.equalsIgnoreCase("Oct"))
            ret=0;
        if(month.equalsIgnoreCase("may"))
            ret=1;
        if(month.equalsIgnoreCase("aug"))
            ret=2;
        if(month.equalsIgnoreCase("feb") ||month.equalsIgnoreCase("mar")||month.equalsIgnoreCase("nov"))
           ret=3;
        if(month.equalsIgnoreCase("jun"))
            ret=4;
        if(month.equalsIgnoreCase("sep")||month.equalsIgnoreCase("dec"))
            ret=5;
        if(month.equalsIgnoreCase("apr")||month.equalsIgnoreCase("jul"))
            ret=6;
    return ret ;
    }
    
    int yearcal(int year)
    {
        int ret1=0;
        if(year>=1600 && year<=1699)
            ret1=6;
        if(year>=1700 && year<=1799)
            ret1=4;
        if(year>=1800 && year<=1899)
            ret1=2;
        if(year>=1900 && year<=1999)
            ret1=0;
        if(year>=2000 && year<=2099)
            ret1=6;
     return ret1;
    }
}

