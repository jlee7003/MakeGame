public class HelloWorld{

//class

static class Player
{
    String name;
    int hp;
    int atk;
    
    //생성자
    public Player(String name, int hp, int atk)
    {
        this.name = name;
        this.hp = hp;
        this.atk = atk;
    }
 
     public void attack(Enemy enemy)
    {
       System.out.println("Player Attack!");
        enemy.hp -= this.atk; //적의 hp는 this(player의 공격력) - 적의 hp
       System.out.println("Enemy hp:" + enemy.hp);        
        //enemy란 객체의 hp를 참조하겠다.
        
        //this는 이 객체의 값을 의미 즉 해당 this가 해당하는 클래스
    }
    
    public boolean isLive(){
        if( hp <= 0)
        {
            return false; //죽었다
        }
        else
        {
            return true; //살았다
        }
    }
   
   
}

static class Enemy
{
    String name;
    int hp;
    int atk;
    
     public Enemy(String name, int hp, int atk)
    {
        this.name = name;
        this.hp = hp;
        this.atk = atk;
    }
    
public void attack(Player player)
{
    System.out.println("Enemy Attack!");
     player.hp -= this.atk;
    System.out.println("Player hp:" + player.hp);   
}

public boolean isLive(){
        if( hp <= 0)
        {
            return false; //죽었다
        }
        else
        {
            return true; //살았다
        }
    }


}


     public static void main(String []args)
     {
         Player player = new Player("gamepari", 100, 12);
         Enemy enemy = new Enemy("Kingkupa", 80, 5);
         
         while(player.isLive() && enemy.isLive())
         {
             player.attack(enemy);
             enemy.attack(player);
         }
         
         if(player.isLive()){
             System.out.println("player WIN");
         }
         else{
             System.out.println("enemy WIN");
         }
         
     }
}
