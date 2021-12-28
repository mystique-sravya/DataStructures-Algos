# DataStructures-Algos
THIS REPOSITORY CONTAIN DATASTRUCTURES ALGORITHMS IN SIMPLE WAY POSSIBLE
>>> BINARY TREE IMPLEMENTATION:
>> ARRAY IMPLEMENTATION
import java.util.*;
public class BinaryTree {
int b[]=new int [100];
   int n =0,data,root;
   char c;
   void create(int data){
       if (b[0]== 0){
           b[0]=data;  //main root node creation
           n++;        // increment of n value, when root is created n=1
       }
       else{
           System.out.println("tree already generated");
       }
   }
   //creating an insert method
   //Here we specify for which root node we insert the child node
   //We also specify at which side should the child node be inserted.
   void insert(int root,int data,char c) {
    int f=0,x,i;
    for(i=0;i<=n;i++) {
    if(b[i]== root) {
    f=1;
    break;
    }
    }
    if(f==0) {
    System.out.println("root node doesnt exist /provide valid root node");
    }
    else {
    if(c=='l'||c=='L') {  // if the given char is l then the node is inserted at left side of root node
    x=2*i+1;
    if(b[x]==0) {
    b[x]=data;
    if(x>n)
    n=x;
    }else {
    System.out.println("already left child is present for root node given");
    }
   
    }else if(c=='r'||c=='R') {  // if the given char is r then the node is inserted at right side of root node
    x=2*i+2;
    if(b[x]==0) {
    b[x]=data;
    if(x>n)
    n=x;
    }
    else{
    System.out.println("already right child is present for root node given");
    }
    }
    }
   }
   //display level order method display the nodes present in binary tree in level order format
   void displayLevelOrder(){
    for(int i=0;i<=n;i++) {
    if(b[i]==0)
    System.out.println("null");
    else
    System.out.println(b[i]+"  ");
    }
   }
   //in-order method displays the binary tree in in-order format ( left - root- right)
   void inorder(int ip)
   {
    if(b[ip] == 0) {
    System.out.println("-");}
    else {
    inorder(2*ip+1);
    System.out.println(b[ip]+" ");
    inorder(2*ip+2);
    }
   }
   //pre-order method displays the binary tree in pre-order format (  root-left- right)
   void preorder(int ip)
   {
    if(b[ip]==0)
    System.out.println("-");
    else {
    System.out.println(b[ip]+" ");
    preorder(2*ip+1);
    preorder(2*ip+2);
    }
   }
   //post-order method displays the binary tree in post-order format ( left- right - root)
   void postorder(int ip)
   {
    if(b[ip]==0)
    System.out.println("-");
    else {
    postorder(2*ip+1);
    postorder(2*ip+2);
    System.out.println(b[ip]+" ");
    }
   }
  //@driver code
   public static void main(String args[]) {
    BinaryTree b = new BinaryTree();
    Scanner s =new Scanner (System.in);
    System.out.print("enter root node:");
    b.create(s.nextInt());
    loop:
    while(true) {
    System.out.println("1.insert \n 2.level-order display \n 3.in-order dispaly \n 4.pre- order dispaly \n 5.post- order display \n 6.exit ");
    int ch =s.nextInt();
    switch(ch) {
    case 1:
    int root = s.nextInt();
    int data = s.nextInt();
    char c=s.next().charAt(0);
    b.insert(root, data, c);
    break;
   
    case 2:
    System.out.println("level-order-display");
    b.displayLevelOrder();
    break;
    case 3:
    System.out.println("in-order-display");
    System.out.println("mention index position:");
    b.inorder(s.nextInt());
    break;
    case 4:
    System.out.println("pre-order-display");
    System.out.println("mention index position:");
    b.preorder(s.nextInt());
    break;
    case 5:
    System.out.println("post-order-display");
    System.out.println("mention index position:");
    b.postorder(s.nextInt());
    break;
    case 6:
    break loop;
    }
    }
    
