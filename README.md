/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package appointment;


import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.DataInputStream;
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.io.Writer;
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;
import java.util.Scanner;
import static org.apache.poi.hssf.usermodel.HeaderFooter.date;
import org.apache.poi.ss.usermodel.Cell;
import org.apache.poi.ss.usermodel.Row;
import org.apache.poi.xssf.usermodel.XSSFSheet;
import org.apache.poi.xssf.usermodel.XSSFWorkbook;

/**
 *
 * @author HP
 */
public class Appointment {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) throws FileNotFoundException, IOException {
        int status = 1,choice,login;int m,cases,id;
        String ids;
        String arrayName[][] = new String[10][5];  
          String Appointment[][] = new String[10][6];  
        String name;
        Scanner input = new Scanner(System.in);
       while(status == 1)
       {
       System.out.println("---------------------------");
       System.out.println("Welcome to appointment bo0king system");
       System.out.println("Login as a patient press 1 or a Visitor press 2:, Pess 3-To view Appotiment reports and visitors report  , Press 4 to view Patient report , Press 5 - to see patients list");
       login = input.nextInt();
       switch(login)
       {
           case 1:
           {
               System.out.println("Welcome patient to the appointment system ");
               System.out.println("Press 1 if already a patient or press 2 if register:");
               cases = input.nextInt();
               switch(cases)
               {
                   case 1:
                       System.out.println("1. Book an treatment appoitnment 2.Cancel an booking");
                       cases = input.nextInt();
                       switch(cases)
                       {
                           case 1:
                               System.out.println("Welcome to book an appointment");
                               System.out.println("");
                              System.out.println("See the pysician time table and book the appointment");
                              FileInputStream record = new FileInputStream(new File("C:\\Users\\HP\\Downloads\\Doctor.xlsx"));
               
                                             XSSFWorkbook workbook = new XSSFWorkbook(record);
               
                                             XSSFSheet tables = workbook.getSheetAt(0);
                                             Iterator<Row> full_row = tables.iterator();
                                              System.out.println("Id             Name               Timming               Day         Room       Consulting hour ");

                                                 while (full_row.hasNext()) 
                                             {
                                                    Row line = full_row.next();
                //For each row, iterate through all the columns
                                                    Iterator<Cell> full_column = line.cellIterator();
                
                 
                                                   while (full_column.hasNext()) 
                                              {
                                                             Cell cell = full_column.next();
                          
                    //Check the cell type and format accordingly
                                                    switch (cell.getCellType()) 
                                                   {
                                                                  case Cell.CELL_TYPE_NUMERIC:
                                                        System.out.print(cell.getNumericCellValue()+ "        ");
                                                                 break;
                                                        case Cell.CELL_TYPE_STRING:
                                                                System.out.print(cell.getStringCellValue() + "        ");
                                                          break;
                                                        }
                }
                System.out.println("  ");
            }
            record.close();
            
            System.out.println("To book the appointment Please enter - your name , Physician name , time , date , day , status,treatment name :");
                       
            for (int i = 0; i < 1; i++)  
            {
               for (int j = 0; j < 6; j++)   {
               Appointment[i][j] = input.nextLine();  
            
        
            }
            }
            StringBuilder creates = new StringBuilder();
           for(int i = 0; i < 1; i++)//for each row
            {
                  for(int j = 0; j < 6; j++)//for each column
                    {
                         creates.append(Appointment[i][j]+"");
                         if(j < Appointment.length - 1)//if this is not the last row element
                         creates.append("  ");//then add comma (if you don't like commas you can use spaces)
                    }
                    creates.append("\n");//append new line at the end of the row
                    
                        File file = new File("C:\\Users\\HP\\Downloads\\Appointment.txt");
                        FileWriter f = new FileWriter(file.getAbsoluteFile(), true);
                        BufferedWriter writer = new BufferedWriter(f);
                        writer.write(creates.toString());//save the string in the file visiotrs .
                        writer.close();
}       
                              
                              
                               
                       }
               }
               
               break;
              
           }
           case 2:
           {
               System.out.println("Welcome Visitor");
               System.out.println("Look up as 1.Expertise  or  2.By physican name");
               choice = input.nextInt();
               switch(choice)
               {
                   case 1:
                   {
                       
                   }
                   case 2:
                   {
                       System.out.println("List of all physicians mame with full list :");
                        FileInputStream record = new FileInputStream(new File("C:\\Users\\HP\\Downloads\\Doctor.xlsx"));
               
                         XSSFWorkbook workbook = new XSSFWorkbook(record);
               
                          XSSFSheet tables = workbook.getSheetAt(0);
                          Iterator<Row> full_row = tables.iterator();
                          System.out.println("Id             Name               Timming               Day         Room       Consulting hour ");

            while (full_row.hasNext()) 
            {
                Row line = full_row.next();
                //For each row, iterate through all the columns
                Iterator<Cell> full_column = line.cellIterator();
                
                 
                while (full_column.hasNext()) 
                {
                    Cell cell = full_column.next();
                          
                    //Check the cell type and format accordingly
                    switch (cell.getCellType()) 
                    {
                        case Cell.CELL_TYPE_NUMERIC:
                            System.out.print(cell.getNumericCellValue()+ "        ");
                            break;
                        case Cell.CELL_TYPE_STRING:
                            System.out.print(cell.getStringCellValue() + "        ");
                           break;
                   }
                }
                System.out.println("  ");
            }
            record.close();
            
            System.out.println("Enter physician name , your name , time , date , treatment name  for which appointmnet needs to fixed :");
           
           
            for (int i = 0; i < 1; i++)  
            {
               for (int j = 0; j < 5; j++)   {
               arrayName[i][j] = input.nextLine();  
            
        
            }
            }
            StringBuilder creates = new StringBuilder();
           for(int i = 0; i < 1; i++)//for each row
            {
                  for(int j = 0; j < 5; j++)//for each column
                    {
                         creates.append(arrayName[i][j]+"");
                         if(j < arrayName.length - 1)//if this is not the last row element
                         creates.append("  ");//then add comma (if you don't like commas you can use spaces)
                    }
                    creates.append("\n");//append new line at the end of the row
                    
                        File file = new File("C:\\Users\\HP\\Downloads\\Visitors.txt");
                        FileWriter f = new FileWriter(file.getAbsoluteFile(), true);
                        BufferedWriter writer = new BufferedWriter(f);
                        writer.write(creates.toString());//save the string in the file visiotrs .
                        writer.close();
}          

                        
                   }
    
                      
                       
           }
            
        
                   
                    
       
   
           break;
           }
           
           case 3:
           {
             System.out.println("Appointments of patients :");
             String fName = "C:\\Users\\HP\\Downloads\\Appointment.txt";
             String thisLine; 
               FileInputStream fis = new FileInputStream(fName);
               DataInputStream myInput = new DataInputStream(fis);
              List<String[]> lines = new ArrayList<String[]>();
              while ((thisLine = myInput.readLine()) != null) {
                 lines.add(thisLine.split(","));
                      }
              String[][] array = new String[lines.size()][0];
              lines.toArray(array);   
              for (int i = 0; i < 1; i++)   
                {   
                    for (int j = 0; j < 1; j++)  { 
 
                     System.out.print(array[i][j] + " ");   
 
                    }
                System.out.println();   
                }   
          
           
          
             
                     
             System.out.println("Visitors appotiments :");
             
             break;
           }
           case 4:
           {
               String fName = "C:\\Users\\HP\\Downloads\\Appointment.txt";
               String thisLine; 
               FileInputStream fis = new FileInputStream(fName);
               DataInputStream myInput = new DataInputStream(fis);
              List<String[]> lines = new ArrayList<String[]>();
              while ((thisLine = myInput.readLine()) != null) {
                 lines.add(thisLine.split(";"));
                      }
                    String[][] array = new String[lines.size()][0];
                    lines.toArray(array);   
                    System.out.println("Enter the patient Id which needs to be shown :");
                    
                       
                   
       break;
       
    }
           case 5:
           {
               System.out.println("Show patient lost");
               FileInputStream record = new FileInputStream(new File("C:\\Users\\HP\\Downloads\\PAtinet.xlsx"));
               
               XSSFWorkbook workbook = new XSSFWorkbook(record);
               
               XSSFSheet tables = workbook.getSheetAt(0);
               Iterator<Row> full_row = tables.iterator();
            while (full_row.hasNext()) 
            {
                Row line = full_row.next();
               
                Iterator<Cell> full_column = line.cellIterator();
                
                 
                while (full_column.hasNext()) 
                {
                    Cell cell = full_column.next();
                    
                    //Check the cell type and format accordingly
                    switch (cell.getCellType()) 
                    {
                        case Cell.CELL_TYPE_NUMERIC:
                            System.out.print(cell.getNumericCellValue()+ "                 ");
                            break;
                        case Cell.CELL_TYPE_STRING:
                            System.out.print(cell.getStringCellValue() + "                  ");
                           break;
                   }
                }
                System.out.println("         ");
            }
            record.close();
            break;
        } 
           }
    
}
    }
    }


