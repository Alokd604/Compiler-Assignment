 
import java.util.*;

public class Assignment2 {
    public static void main(String[] args) {
        Scanner sc= new Scanner(System.in);    //System.in is a standard input stream
        String[][] arr=new String[100][100];
        int sl_no=0;

        System.out.println("For INSERT press 1\nFor REMOVE press 2\nFor UPDATE press 3\nFor DISPLAY press4");
        System.out.print("Enter Choice: ");
        String var = sc.next();
        while (true) {
            if(var.equals("1")){
                sl_no=insert(arr,sl_no);
            }

            else  if(var.equals("2")){
                if(sl_no==0)
                    System.out.println("Table is Empty.please Insert data first");
                else{
                    System.out.println("Which Variable you want to remove: ");
                    String remove_name = sc.next();
                    int remove_index=0;
                    for (int i=0;i<sl_no;i++){
                        if(arr[i][2].equals(remove_name)){
                            remove_index=i;
                            break;
                        }
                    }
                    for (int i=remove_index;i<(sl_no-1);i++){
//                        arr[i][0]=arr[i+1][0];
                        arr[i][1]=arr[i+1][1];
                        arr[i][2]=arr[i+1][2];
                        arr[i][3]=arr[i+1][3];
                    }
                    sl_no--;
                }

            }

            else if(var.equals("3")){
                if(sl_no==0)
                    System.out.println("Table is Empty.please Insert data first");
                else{
                    System.out.println("Which Variable you want to update: ");
                    String update_name = sc.next();
                    System.out.println("Enter update data Type: ");
                    String update_type=sc.next();
                    System.out.println("Enter updated Value: ");
                    String update_value= sc.next();
                    for (int i=0;i<sl_no;i++){
                        if(arr[i][2].equals(update_name)){
                            arr[i][1]=update_type;
                            arr[i][3]=update_value;
                            break;
                        }

                    }
                }

            }
            else if(var.equals("4")){
        System.out.println("sl\ttype\tname\tvalue ");
        for (int i=0;i<sl_no;i++){
                System.out.println(arr[i][0]+"\t"+arr[i][1]+"\t"+arr[i][2]+"\t\t"+arr[i][3]);

        }

            }

            else if(var.equals("5"))
                break;
            else {
                System.out.println("Not correct choice");
            }
            System.out.println("For INSERT press 1\nFor REMOVE press 2\nFor UPDATE press 3\nFor DISPLAY press4");
            System.out.print("Enter Choice: ");
            var= sc.next();
        }

    }

    public static int insert(String[][] main_arr,int index) {
        System.out.println("Enter Input: ");
        Scanner sc = new Scanner(System.in);
        String str = sc.nextLine();
        String[] new_str = str.split(" ");
        String type = new_str[0];
        String name_data = new_str[1];
        String name = null, value = null;
        System.out.println(type + " & " + name_data);
        int single_var = 1;
        for (int i = 0; i < str.length(); i++) {
            if (str.charAt(i) == ',') {
                single_var = 0; //means its a multiple variable object
                break;
            }
        }
        if (single_var == 1) {
//            System.out.println("its a single variable object");
            if (name_data.length() == 1) {
//                System.out.println("Name="+name_data+" "+"value=NULL");
                name = name_data;
                value = "NULL";
                main_arr[index][0] = Integer.toString(index + 1);
                main_arr[index][1] = type;
                main_arr[index][2] = name;
                main_arr[index][3] = value;
//                System.out.println(main_arr[index][0] + " " + main_arr[index][1] + " " + main_arr[index][2] + " " + main_arr[index][3]);
                index++;
            } else {
                String[] str1 = name_data.split("=");
                name = str1[0];
                value = str1[1];
//                System.out.println("Name="+name+" "+"value="+value);
                main_arr[index][0] = Integer.toString(index + 1);
                main_arr[index][1] = type;
                main_arr[index][2] = name;
                main_arr[index][3] = value;
//                System.out.println(main_arr[index][0] + " " + main_arr[index][1] + " " + main_arr[index][2] + " " + main_arr[index][3]);
                index++;
            }

        } else {
//            System.out.println("its a multiple var object");
            String[] words = name_data.split(",");
            for (int i = 0; i < words.length; i++) {
//                System.out.println(words[i]+" ");
                if (words[i].length() == 1) {
//                    System.out.println("Name="+words[i]+" "+"value=NULL");
                    name = words[i];
                    value = "NULL";
                    main_arr[index][0] = Integer.toString(index + 1);
                    main_arr[index][1] = type;
                    main_arr[index][2] = name;
                    main_arr[index][3] = value;
//                    System.out.println(main_arr[index][0] + " " + main_arr[index][1] + " " + main_arr[index][2] + " " + main_arr[index][3]);
                    index++;
                } else {
                    String[] str2 = words[i].split("=");
                    name = str2[0];
                    value = str2[1];
//                    System.out.println("Name="+name+" "+"value="+value);
                    main_arr[index][0] = Integer.toString(index + 1);
                    main_arr[index][1] = type;
                    main_arr[index][2] = name;
                    main_arr[index][3] = value;
//                    System.out.println(main_arr[index][0] + " " + main_arr[index][1] + " " + main_arr[index][2] + " " + main_arr[index][3]);
                     index++;
                }

            }
        }

    return index;
    }


}
