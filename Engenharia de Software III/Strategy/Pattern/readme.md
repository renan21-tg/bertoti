<img width="1015" height="397" alt="image" src="https://github.com/user-attachments/assets/1e008700-7e9f-4c33-bf54-d389d8f5723e" />

<br><br>

***PaymentStrategy.java***

    public interface PaymentStrategy {
        // paga e retorna mensagem/desfecho
        String pay(double amount);
    }

<br><br>

***CreditCardStrategy.java***

    public class CreditCardStrategy implements PaymentStrategy {
        private final String cardNumber;
    
        public CreditCardStrategy(String cardNumber) {
            this.cardNumber = cardNumber;
        }
    
        @Override
        public String pay(double amount) {
            // simulação de processamento
            return "Pagamento com cartão (" + mask(cardNumber) + ") de R$" + amount + " realizado.";
        }
    
        private String mask(String card) {
            if (card == null || card.length() < 4) return "****";
            return "**** **** **** " + card.substring(card.length() - 4);
        }
    }

<br><br>

***PaypalStrategy.java***
    
    public class PaypalStrategy implements PaymentStrategy {
        private final String email;
    
        public PaypalStrategy(String email) {
            this.email = email;
        }
    
        @Override
        public String pay(double amount) {
            return "Pagamento via PayPal (" + email + ") de R$" + amount + " realizado.";
        }
    }

<br><br>

***BankTransferStrategy .java***

    public class BankTransferStrategy implements PaymentStrategy {
        private final String account;
    
        public BankTransferStrategy(String account) {
            this.account = account;
        }
    
        @Override
        public String pay(double amount) {
            return "Transferência bancária da conta " + account + " no valor de R$" + amount + " iniciada.";
        }
    }

<br><br>

***PaymentService.java***

    public class PaymentService {
        private PaymentStrategy strategy;
    
        public PaymentService(PaymentStrategy initialStrategy) {
            this.strategy = initialStrategy;
        }
    
        public void setStrategy(PaymentStrategy strategy) {
            this.strategy = strategy;
        }
    
        public String executePayment(double amount) {
            if (strategy == null) {
                throw new IllegalStateException("Nenhuma PaymentStrategy configurada.");
            }
            return strategy.pay(amount);
        }
    
        // Demo de uso
        public static void main(String[] args) {
            PaymentService service = new PaymentService(new CreditCardStrategy("1234123412341234"));
            System.out.println(service.executePayment(200.0));
    
            // trocando a strategy em tempo de execução:
            service.setStrategy(new PaypalStrategy("usuario@exemplo.com"));
            System.out.println(service.executePayment(75.5));
    
            // outra troca:
            service.setStrategy(new BankTransferStrategy("BR1234567890"));
            System.out.println(service.executePayment(1000.0));
        }
    }
