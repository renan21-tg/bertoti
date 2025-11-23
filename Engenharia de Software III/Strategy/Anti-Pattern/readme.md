<img width="741" height="382" alt="image" src="https://github.com/user-attachments/assets/8debe5ab-d5ac-46ba-9512-779fa77c53cc" />

<br><br>

***PaymentProcessor.java***

    public abstract class PaymentProcessor {
    protected String payer;

    public PaymentProcessor(String payer) {
        this.payer = payer;
    }

    public abstract String process(double amount);
    }

<br><br>

***CreditCardProcessor.java***

    public class CreditCardProcessor extends PaymentProcessor {
    
        public CreditCardProcessor(String payer) {
            super(payer);
        }
    
        @Override
        public String process(double amount) {
            return "Pagamento com cartão de crédito de R$" + amount + " realizado por " + payer;
        }
    }

<br><br>

***PaypalProcessor.java***

    public class PaypalProcessor extends PaymentProcessor {
    
        public PaypalProcessor(String payer) {
            super(payer);
        }
    
        @Override
        public String process(double amount) {
            return "Pagamento via PayPal de R$" + amount + " realizado por " + payer;
        }
    }

<br><br>

***BankTransferProcessor.java***

    public class BankTransferProcessor extends PaymentProcessor {
    
        public BankTransferProcessor(String payer) {
            super(payer);
        }
    
        @Override
        public String process(double amount) {
            return "Transferência bancária de R$" + amount + " iniciada por " + payer;
        }
    }

<br><br>

***PaymentController.java***

    public class PaymentController {
    
        public String checkout(String method, String payer, double amount) {
            PaymentProcessor processor;
            if ("credit".equalsIgnoreCase(method)) {
                processor = new CreditCardProcessor(payer);
            } else if ("paypal".equalsIgnoreCase(method)) {
                processor = new PaypalProcessor(payer);
            } else if ("bank".equalsIgnoreCase(method)) {
                processor = new BankTransferProcessor(payer);
            } else {
                throw new IllegalArgumentException("Método de pagamento não suportado: " + method);
            }
    
            return processor.process(amount);
        }
    
        public static void main(String[] args) {
            PaymentController controller = new PaymentController();
            System.out.println(controller.checkout("credit", "João", 150.0));
            System.out.println(controller.checkout("paypal", "Maria", 42.5));
        }
    }
