<img width="310" height="465" alt="image" src="https://github.com/user-attachments/assets/2bb0b3e8-6708-45f0-8242-a8c13e4cd675" />

<br><br>

***TaskMode.java***

    import java.util.ArrayList;
    import java.util.List;
    
    public class TaskModel {
    
        private List<String> tasks = new ArrayList<>();
    
        public void addTask(String task) {
            tasks.add(task);
        }
    
        public void removeTask(String task) {
            tasks.remove(task);
        }
    
        public List<String> getTasks() {
            return tasks;
        }
    }

<br><br>

***TaskView.java***

    import java.util.List;
    
    public class TaskView {
    
        public void displayTasks(List<String> tasks) {
            System.out.println("===== Lista de Tarefas =====");
            tasks.forEach(System.out::println);
            System.out.println("============================");
        }
    }

<br><br>

***TaskController.java***

    public class TaskController {
    
        private TaskModel model;
        private TaskView view;
    
        public TaskController(TaskModel model, TaskView view) {
            this.model = model;
            this.view = view;
        }
    
        public void addTask(String task) {
            model.addTask(task);
            updateView();
        }
    
        public void removeTask(String task) {
            model.removeTask(task);
            updateView();
        }
    
        public void updateView() {
            view.displayTasks(model.getTasks());
        }
    }

<br><br>

***Main.java***

    public class Main {
        public static void main(String[] args) {
            TaskModel model = new TaskModel();
            TaskView view = new TaskView();
            TaskController controller = new TaskController(model, view);
    
            controller.addTask("Estudar MVC");
            controller.addTask("Treinar Java");
            controller.removeTask("Estudar MVC");
        }
    }
