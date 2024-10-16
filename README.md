# LISTA-3-FABRICIO
1. Foi feita uma pesquisa sobre a audiência de canal de TV em várias casas de uma cidade, em
determinado dia. Para cada casa consultada foi fornecido o número do canal (4, 5, 7, 12) e o
número de pessoas que estavam assistindo aquele canal. Se a televisão estivesse desligada, nada
era anotado, ou seja, essa casa não entrava na pesquisa. Faça um programa que:
• leia um número indeterminado de dados (número do canal e número de pessoas que estavam assistindo); e
• calcule e mostre a porcentagem de audiência de cada canal.
Para encerrar a entrada de dados, digite o número do canal ZERO.

import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;
public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Map<Integer, Integer> audiencia = new HashMap<>();
        int totalPessoas = 0;

        System.out.println("Digite o número do canal (4, 5, 7, 12) e o número de pessoas assistindo. Para encerrar, digite 0.");

        while (true) {
            System.out.print("Número do canal: ");
            int canal = scanner.nextInt();

            if (canal == 0) {
                break; // Encerrar a entrada de dados
            }

            if (canal == 4 || canal == 5 || canal == 7 || canal == 12) {
                System.out.print("Número de pessoas assistindo: ");
                int pessoas = scanner.nextInt();

                audiencia.put(canal, audiencia.getOrDefault(canal, 0) + pessoas);
                totalPessoas += pessoas;
            } else {
                System.out.println("Canal inválido. Digite um dos canais válidos (4, 5, 7, 12).");
            }
        }

        System.out.println("\nPorcentagem de audiência de cada canal:");
        for (int canal : audiencia.keySet()) {
            double porcentagem = (audiencia.get(canal) / (double) totalPessoas) * 100;
            System.out.printf("Canal %d: %.2f%%\n", canal, porcentagem);
        }

        if (totalPessoas == 0) {
            System.out.println("Nenhuma audiência registrada.");
        }

        scanner.close();
    }
}

2. Faça um programa que apresente o menu de opções a seguir:
Menu de opções:
1. Média aritmética
2. Média ponderada
3. Sair
Digite a opção desejada.
Na opção 1: receber duas notas, calcular e mostrar a média aritmética.
Na opção 2: receber três notas e seus respectivos pesos, calcular e mostrar média ponderada.
Na opção 3: sair do programa.
Verifique a possibilidade de opção inválida. Nesse caso, o programa deverá mostrar uma mensagem.

import java.util.Scanner;
public class Main {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        int entrada;
        do {


            System.out.println("""
                    Menu de opções:
                    1. Média aritmética
                    2. Média ponderada
                    3. Sair
                    """);
            entrada = input.nextInt();
            if (entrada == 1) {
                Mediaaritmetica opcao1 = new Mediaaritmetica();
            } else if (entrada == 2) {
                Mediaponderada opcao2 = new Mediaponderada();
            } else if (entrada == 3) {
                System.out.println("Obrigado por utilizar!");
            }

        } while (entrada != 3);
        input.close();
    }
}
import java.util.Scanner;

public class Mediaaritmetica {
    private double nota1;
    private double nota2;
    Scanner input = new Scanner(System.in);

    public Mediaaritmetica() {
        Obternotas();
        CalcularMedia();
    }

    public void Obternotas() {
        System.out.println("Digite a primeira nota: ");
        nota1 = input.nextDouble();
        System.out.println("Digite a segunda nota: ");
        nota2 = input.nextDouble();
        System.out.println();
    }

    public void CalcularMedia() {
        double media = (nota1 + nota2) / 2;
        System.out.printf("A media entre as notas é de: %.2f%n", media);
    }
}
import java.util.Scanner;

public class Mediaponderada {
    private double nota1;
    private double nota2;
    private double nota3;
    private int peso1;
    private int peso2;
    private int peso3;
    Scanner input = new Scanner(System.in);

    public Mediaponderada() {
        Obternotas();
        Calcularnotas();

    }

    public void Obternotas() {
        System.out.println("Digite a primeira nota: ");
        nota1 = input.nextDouble();
        System.out.println("Digite o peso da nota: ");
        peso1 = input.nextInt();
        System.out.println("Digtite a segunda nota: ");
        nota2 = input.nextDouble();
        System.out.println("Digite o peso da nota: ");
        peso2 = input.nextInt();
        System.out.println("Digite a terceira nota: ");
        nota3 = input.nextDouble();
        System.out.println("Digite o peso da nota: ");
        peso3 = input.nextInt();
    }

    public void Calcularnotas() {
        double media = ((nota1 * peso1) + (nota2 * peso2) + (nota3 * peso3) / (peso1 + peso2 + peso3));
        System.out.printf("Sua média levando em consideração a a média pondera é de: %.2f%n", media);
    }

}

3. Faça um programa que receba dez idades, pesos e alturas, calcule e mostre:
• a média das idades das dez pessoas;
• o total que possui superior a 90 kg e altura inferior a 1,50 metro;
• a porcentagem de pessoas com idade entre 10 e 30 anos entre aquelas que medem mais de
1,90 m;
1
• uma opção para apresentar todos os dados coletados;

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        int[] idades = new int[10];
        double[] alturas = new double[10];
        double[] pesos = new double[10];
        int contadorPesoAltura = 0;
        int totalIdade = 0;
        int contadorPesoAltura2 = 0;


        for (int i = 0; i < idades.length; i++) {
            System.out.print("Idade da pessoa " + (i + 1) + ": ");
            idades[i] = input.nextInt();
            totalIdade += idades[i];
        }


        double mediaIdade = (double) totalIdade / idades.length;
        System.out.printf("A média das idades é de: %.2f anos%n", mediaIdade);


        for (int i = 0; i < alturas.length; i++) {
            System.out.print("Altura da pessoa " + (i + 1) + " (em metros): ");
            alturas[i] = input.nextDouble();
            System.out.print("Peso da pessoa " + (i + 1) + " (em kg): ");
            pesos[i] = input.nextDouble();


            if (pesos[i] > 90 && alturas[i] < 1.50) {
                contadorPesoAltura++;
            }
            if (idades[i] > 10 && idades[i] < 30 && alturas[i] > 1.90) {
                contadorPesoAltura2++;
            }
        }

        System.out.println("Total de pessoas com peso superior a 90 kg e altura inferior a 1,50 m: " + contadorPesoAltura);
        System.out.println("Total de pessoas com idade entre 10 e 30 e altura maior que a 1,90 m: " + contadorPesoAltura2);

        input.close();
    }
}

4. Fazer um algoritmo, utilizando o comando for, que calcule e escreva a soma dos 50 primeiros
termos da seguinte série: S = 1000/1 − 997/2 + 994/3 − 991/4 + . . .


public class Main {
    public static void main(String[] args) {
        double soma = 0.0;

        for (int i = 1; i <= 50; i++) {

            double numerador = 1000 - (3 * (i - 1));

            if (i % 2 == 0) {
                soma -= numerador / i;
            } else {
                soma += numerador / i;
            }
        }

        System.out.printf("A soma dos 50 primeiros termos da série é: %.2f%n", soma);
    }
}

5. Criar a estrutura de dados para armazenar os médicos cadastrados no sistema. (Array List)

public class Medico {
    private String nome;
    private String crm;
    private String especialidade;
    private String telefone;

    
    public Medico(String nome, String crm, String especialidade, String telefone) {
        this.nome = nome;
        this.crm = crm;
        this.especialidade = especialidade;
        this.telefone = telefone;
    }

   
    public String getNome() {
        return nome;
    }

    public String getCrm() {
        return crm;
    }

    public String getEspecialidade() {
        return especialidade;
    }

    public String getTelefone() {
        return telefone;
    }

    
    public String toString() {
        return "Médico{" +
                "nome='" + nome + '\'' +
                ", crm='" + crm + '\'' +
                ", especialidade='" + especialidade + '\'' +
                ", telefone='" + telefone + '\'' +
                '}';
    }
}

import java.util.ArrayList;
import java.util.Scanner;

public class SistemaMedico {
    public static void main(String[] args) {
        ArrayList<Medico> medicos = new ArrayList<>();
        Scanner scanner = new Scanner(System.in);
        String opcao;

        do {
            System.out.println("Cadastro de Médicos");
            System.out.print("Digite o nome do médico: ");
            String nome = scanner.nextLine();
            System.out.print("Digite o CRM do médico: ");
            String crm = scanner.nextLine();
            System.out.print("Digite a especialidade do médico: ");
            String especialidade = scanner.nextLine();
            System.out.print("Digite o telefone do médico: ");
            String telefone = scanner.nextLine();

           
            Medico medico = new Medico(nome, crm, especialidade, telefone);
            medicos.add(medico);

            System.out.print("Deseja cadastrar outro médico? (s/n): ");
            opcao = scanner.nextLine();

        } while (opcao.equalsIgnoreCase("s"));

        
        System.out.println("\nMédicos cadastrados:");
        for (Medico m : medicos) {
            System.out.println(m);
        }

        scanner.close();
    }
}


6. Criar a estrutura de dados para armazenar os dados dos pacientes cadastrados no sistema.
(Array List)

public class Paciente {
    private String nome;
    private String cpf;
    private int idade;
    private String telefone;

    
    public Paciente(String nome, String cpf, int idade, String telefone) {
        this.nome = nome;
        this.cpf = cpf;
        this.idade = idade;
        this.telefone = telefone;
    }

    
    public String getNome() {
        return nome;
    }

    public String getCpf() {
        return cpf;
    }

    public int getIdade() {
        return idade;
    }

    public String getTelefone() {
        return telefone;
    }

    @Override
    public String toString() {
        return "Paciente{" +
                "nome='" + nome + '\'' +
                ", cpf='" + cpf + '\'' +
                ", idade=" + idade +
                ", telefone='" + telefone + '\'' +
                '}';
    }
}

import java.util.ArrayList;
import java.util.Scanner;

public class SistemaPaciente {
    public static void main(String[] args) {
        ArrayList<Paciente> pacientes = new ArrayList<>();
        Scanner scanner = new Scanner(System.in);
        String opcao;

        do {
            System.out.println("Cadastro de Pacientes");
            System.out.print("Digite o nome do paciente: ");
            String nome = scanner.nextLine();
            System.out.print("Digite o CPF do paciente: ");
            String cpf = scanner.nextLine();
            System.out.print("Digite a idade do paciente: ");
            int idade = scanner.nextInt();
            scanner.nextLine();  // Consome a nova linha pendente
            System.out.print("Digite o telefone do paciente: ");
            String telefone = scanner.nextLine();

           
            Paciente paciente = new Paciente(nome, cpf, idade, telefone);
            pacientes.add(paciente);

            System.out.print("Deseja cadastrar outro paciente? (s/n): ");
            opcao = scanner.nextLine();

        } while (opcao.equalsIgnoreCase("s"));

        
        System.out.println("\nPacientes cadastrados:");
        for (Paciente p : pacientes) {
            System.out.println(p);
        }

        scanner.close();
    }
}

7. Criar um algoritmo para auxiliar na lojinha do Sr. Abu.
(a) O sistema deve permitir o cadastro de produtos. Cada item possui código único, nome,
valor unitário e tipo de unidade.
(b) Permitir o cadastro, alteração e a exclusão de produtos.
(c) Realizar a venda, para isso, é necessário informar o código do produto, e a quantidade.
Deve existir a opção de finalizar a compra.
(d) Definir a forma de pagamento
i. Pix - Mostrar o código.
ii. Cartão - Crédito ou débito - Solicitar os dados para pagamento
iii. Dinheiro - Solicitar o valor pago e informar o troco

public class Produto {
    private int codigo;
    private String nome;
    private double valorUnitario;
    private String tipoUnidade;

    public Produto(int codigo, String nome, double valorUnitario, String tipoUnidade) {
        this.codigo = codigo;
        this.nome = nome;
        this.valorUnitario = valorUnitario;
        this.tipoUnidade = tipoUnidade;
    }

    public int getCodigo() {
        return codigo;
    }

    public String getNome() {
        return nome;
    }

    public double getValorUnitario() {
        return valorUnitario;
    }

    public String getTipoUnidade() {
        return tipoUnidade;
    }

    public void setNome(String nome) {
        this.nome = nome;
    }

    public void setValorUnitario(double valorUnitario) {
        this.valorUnitario = valorUnitario;
    }

    public void setTipoUnidade(String tipoUnidade) {
        this.tipoUnidade = tipoUnidade;
    }

   
    public String toString() {
        return "Produto{" +
                "codigo=" + codigo +
                ", nome='" + nome + '\'' +
                ", valorUnitario=" + valorUnitario +
                ", tipoUnidade='" + tipoUnidade + '\'' +
                '}';
    }
}

import java.util.ArrayList;
import java.util.Scanner;

public class LojinhaAbu {
    private static ArrayList<Produto> produtos = new ArrayList<>();
    private static Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        int opcao;
        do {
            System.out.println("\nMenu da Lojinha do Sr. Abu");
            System.out.println("1. Cadastrar Produto");
            System.out.println("2. Alterar Produto");
            System.out.println("3. Excluir Produto");
            System.out.println("4. Vender Produto");
            System.out.println("5. Sair");
            System.out.print("Escolha uma opção: ");
            opcao = scanner.nextInt();
            scanner.nextLine(); // Consumir a nova linha

            switch (opcao) {
                case 1:
                    cadastrarProduto();
                    break;
                case 2:
                    alterarProduto();
                    break;
                case 3:
                    excluirProduto();
                    break;
                case 4:
                    realizarVenda();
                    break;
                case 5:
                    System.out.println("Saindo...");
                    break;
                default:
                    System.out.println("Opção inválida!");
            }
        } while (opcao != 5);
    }

    private static void cadastrarProduto() {
        System.out.print("Digite o código do produto: ");
        int codigo = scanner.nextInt();
        scanner.nextLine(); 
        System.out.print("Digite o nome do produto: ");
        String nome = scanner.nextLine();
        System.out.print("Digite o valor unitário do produto: ");
        double valorUnitario = scanner.nextDouble();
        scanner.nextLine(); 
        System.out.print("Digite o tipo de unidade do produto: ");
        String tipoUnidade = scanner.nextLine();

        produtos.add(new Produto(codigo, nome, valorUnitario, tipoUnidade));
        System.out.println("Produto cadastrado com sucesso!");
    }

    private static void alterarProduto() {
        System.out.print("Digite o código do produto que deseja alterar: ");
        int codigo = scanner.nextInt();
        scanner.nextLine(); 
        for (Produto produto : produtos) {
            if (produto.getCodigo() == codigo) {
                System.out.print("Novo nome: ");
                produto.setNome(scanner.nextLine());
                System.out.print("Novo valor unitário: ");
                produto.setValorUnitario(scanner.nextDouble());
                scanner.nextLine(); 
                System.out.print("Novo tipo de unidade: ");
                produto.setTipoUnidade(scanner.nextLine());
                System.out.println("Produto alterado com sucesso!");
                return;
            }
        }
        System.out.println("Produto não encontrado!");
    }

    private static void excluirProduto() {
        System.out.print("Digite o código do produto que deseja excluir: ");
        int codigo = scanner.nextInt();
        produtos.removeIf(produto -> produto.getCodigo() == codigo);
        System.out.println("Produto excluído com sucesso!");
    }

    private static void realizarVenda() {
        System.out.print("Digite o código do produto para venda: ");
        int codigo = scanner.nextInt();
        System.out.print("Digite a quantidade: ");
        int quantidade = scanner.nextInt();

        for (Produto produto : produtos) {
            if (produto.getCodigo() == codigo) {
                double totalVenda = produto.getValorUnitario() * quantidade;
                System.out.println("Total da venda: R$ " + totalVenda);
                
                System.out.println("Forma de pagamento:");
                System.out.println("1. Pix");
                System.out.println("2. Cartão (Crédito ou Débito)");
                System.out.println("3. Dinheiro");
                System.out.print("Escolha uma forma de pagamento: ");
                int formaPagamento = scanner.nextInt();

                switch (formaPagamento) {
                    case 1:
                        System.out.println("Código para Pix: " + codigo);
                        break;
                    case 2:
                        System.out.print("Digite os dados do cartão: ");
                        String dadosCartao = scanner.next();
                        System.out.println("Pagamento realizado com sucesso usando o cartão: " + dadosCartao);
                        break;
                    case 3:
                        System.out.print("Valor pago: ");
                        double valorPago = scanner.nextDouble();
                        double troco = valorPago - totalVenda;
                        if (troco < 0) {
                            System.out.println("Valor insuficiente!");
                        } else {
                            System.out.printf("Troco: R$ %.2f%n", troco);
                        }
                        break;
                    default:
                        System.out.println("Forma de pagamento inválida!");
                }
                return;
            }
        }
        System.out.println("Produto não encontrado!");
    }
}
