<img width="568" height="312" alt="image" src="https://github.com/user-attachments/assets/72addaf3-1f82-4354-877e-bbb20dc31056" />

<br><br>

***TaskModel.java***

    import java.util.ArrayList;
    import java.util.List;
    
    public class TaskModel {
    
        private List<String> tasks = new ArrayList<>();
        private TaskView view;
    
        public TaskModel(TaskView view) {
            this.view = view;
        }
    
        public void addTask(String task) {
            tasks.add(task);
            updateView(); // Model chamando a View diretamente (ERRADO)
        }
    
        public void removeTask(String task) {
            tasks.remove(task);
            updateView(); // duplo acoplamento
        }
    
        public List<String> getTasks() {
            return tasks;
        }
    
        public void updateView() {
            view.showTasks(tasks);
        }
    }

<br><br>

***TaskView .java***

    import java.util.List;
    
    public class TaskView {
    
        private TaskModel model;
    
        public TaskView(TaskModel model) {
            this.model = model;
        }
    
        public void showTasks(List<String> tasks) {
            System.out.println("===== Lista de Tarefas =====");
            tasks.forEach(System.out::println);
        }
    
        public void addTask(String task) {
            model.addTask(task); // View chamando o Model diretamente (ERRADO)
        }
    
        public void removeTask(String task) {
            model.removeTask(task);
        }
    }

<br><br>

***Main.java***

    public class Main {
        public static void main(String[] args) {
            TaskView view = new TaskView(null);
            TaskModel model = new TaskModel(view);
            view = new TaskView(model);
    
            view.addTask("Estudar MVC");
            view.addTask("Praticar Java");
            view.removeTask("Estudar MVC");
        }
    }
