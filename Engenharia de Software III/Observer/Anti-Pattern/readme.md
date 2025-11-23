<img width="278" height="350" alt="image" src="https://github.com/user-attachments/assets/ec671775-1434-44a0-9277-fcb72a925f33" />

<br><br>

***User.java***

      public class User {
          private String name;
          private String lastPost;
      
          public User(String name) {
              this.name = name;
          }
      
          public void post(String message) {
              this.lastPost = message;
              System.out.println(name + " publicou: " + message);
          }
      
          public String getLastPost() {
              return lastPost;
          }
      
          public String getName() {
              return name;
          }
      }

<br><br>

***Follower.java***

      public class Follower {
          private String name;
          private User userFollowed;
      
          public Follower(String name, User userFollowed) {
              this.name = name;
              this.userFollowed = userFollowed;
          }
      
          // precisa consultar manualmente — nada é automático
          public void checkUpdates() {
              System.out.println(name + " verificando postagens de " + userFollowed.getName());
              System.out.println("Última postagem: " + userFollowed.getLastPost());
          }
      }

<br><br>

***Main.java***

      public class Main {
          public static void main(String[] args) {
              User user = new User("Alice");
              Follower follower = new Follower("Bob", user);
      
              user.post("Olá, mundo!");
              follower.checkUpdates();  // precisa consultar manualmente
          }
      }
