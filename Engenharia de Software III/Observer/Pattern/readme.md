<img width="374" height="618" alt="image" src="https://github.com/user-attachments/assets/a3ebd1e1-8bdd-4548-804d-feab39bb783e" />

<br><br>

***Observer.java***

    public interface Observer {
        void update(String userName, String message);
    }

<br><br>

***Subject.java***

    public interface Subject {
        void attach(Observer observer);
        void detach(Observer observer);
        void notifyObservers(String message);
    }

<br><br>

***User.java***

    import java.util.ArrayList;
    import java.util.List;
    
    public class User implements Subject {
    
        private String name;
        private List<Observer> followers = new ArrayList<>();
    
        public User(String name) {
            this.name = name;
        }
    
        @Override
        public void attach(Observer observer) {
            followers.add(observer);
        }
    
        @Override
        public void detach(Observer observer) {
            followers.remove(observer);
        }
    
        @Override
        public void notifyObservers(String message) {
            for (Observer follower : followers) {
                follower.update(name, message);
            }
        }
    
        public void post(String message) {
            System.out.println(name + " publicou: " + message);
            notifyObservers(message);
        }
    
        public String getName() {
            return name;
        }
    }

<br><br>

***Follower.java***

    public class Follower implements Observer {
    
        private String name;
    
        public Follower(String name) {
            this.name = name;
        }
    
        @Override
        public void update(String userName, String message) {
            System.out.println(name + " recebeu notificação:");
            System.out.println(" - " + userName + " publicou: " + message);
        }
    }

<br><br>

***Main.java***

    public class Main {
        public static void main(String[] args) {
            User user = new User("Alice");
    
            Follower bob = new Follower("Bob");
            Follower charlie = new Follower("Charlie");
    
            user.attach(bob);
            user.attach(charlie);
    
            user.post("Olá, seguidores!");
        }
    }
