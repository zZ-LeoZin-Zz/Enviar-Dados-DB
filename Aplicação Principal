import javax.swing.*;
import java.sql.Connection;
import javax.swing.JOptionPane;
import java.util.List;



public class AplicacaoPrincipal {



    public static void main(String[] args) {
        Conexao conexao = new Conexao();
        Connection conn = conexao.conectar();

        List<List<String>> tabela = Conexao.Exibir(conn, "cliente");

        boolean condicao = true;

        while (condicao) {


            Object[] itens = {"Incluir", "Excluir", "Alterar", "Exibir"};
            Object selecionarValor = JOptionPane.showInputDialog(null, "Escolha sua ação", "Opção", JOptionPane.INFORMATION_MESSAGE, null, itens, itens[0]);

            if (selecionarValor == null) {
                JOptionPane.showMessageDialog(null, "Adeus");

                break;
            } else {
                System.out.println("\n Entrando na opção seleionada");
            }

            if (selecionarValor == "Incluir") {

                //Definir o painel de exibição
                JTextField nome = new JTextField(20);
                JTextField email = new JTextField(25);
                JTextField telefone = new JTextField(20);

                JPanel myPanel = new JPanel();

                myPanel.add(new JLabel("Digite seu nome:"));
                myPanel.add(nome);
                myPanel.add(Box.createHorizontalStrut(15)); // a spacer
                myPanel.add(new JLabel("Digite seu email:"));
                myPanel.add(email);
                myPanel.add(Box.createHorizontalStrut(15)); // a spacer
                myPanel.add(new JLabel("Digite seu telefone:"));
                myPanel.add(telefone);

                //Validação, comando de repetição e envio de dados para o database
                while (condicao) {
                    int result = JOptionPane.showConfirmDialog(null, myPanel, "Coloque os dados requiridos", JOptionPane.OK_CANCEL_OPTION);
                    if (result == JOptionPane.OK_OPTION) {
                        System.out.println("Nome: " + nome.getText());
                        System.out.println("Email: " + email.getText());
                        System.out.println("Telefone" + telefone.getText());

                        String nomee = nome.getText();
                        String emaill = email.getText();
                        String telefonee = telefone.getText();
                        conexao.incluir(conn, nomee, emaill, telefonee);

                        // Limpar os campos para a próxima repetição
                        nome.setText("");
                        email.setText("");
                        telefone.setText("");

                    } else break; //sai do loop
                }


            }

            if (selecionarValor == "Excluir") {
                for (List<String> linha : tabela) {
                    System.out.println(String.join(", ", linha));
                }

                int ID;

                while (condicao) {
                    String option = JOptionPane.showInputDialog(null, "Digite o valor");
                    if (option == null) {

                        System.out.println("\n Voltando a pagina inicial");
                        break;


                    } else {
                        ID = Integer.parseInt(option);
                        conexao.excluir(conn, ID);
                    }
                }
            }

            if (selecionarValor == "Exibir") {

                for (List<String> linha : tabela) {
                    System.out.println(String.join(", ", linha));
                }

            }

            if (selecionarValor == "Alterar") {
                int ID = 0;

                for (List<String> linha : tabela) {
                    System.out.println(String.join(", ", linha));
                }
                while (condicao) {
                    String id = JOptionPane.showInputDialog(null,"Digite o ID que deseja alterar");
                    if (id == null) {
                        break;
                    }else {
                        ID = Integer.parseInt(id);
                        Object[] Option = {"Nome", "Email", "Telefone"};

                        int escolha = JOptionPane.showOptionDialog(null, "Escolha o que deseja alterar", "Escolha", JOptionPane.DEFAULT_OPTION, JOptionPane.WARNING_MESSAGE, null, Option, Option[0]);


                        if (escolha == 0)/*0 = Nome*/ {
                            while (condicao) {
                                String nome = JOptionPane.showInputDialog(null, "Digite o novo nome: ");
                                if(nome == null){break;}
                                int simnao = JOptionPane.showConfirmDialog(null, "Voce Digitou: " + nome + " Está correto ?", "Confirmação", JOptionPane.YES_NO_OPTION);
                                if (simnao == 0) {
                                    conexao.alterar1(conn, ID, nome);
                                    break;
                                }
                                if (simnao == 1) {
                                    JOptionPane.showMessageDialog(null, "Então vamos recomeçar");
                                }
                            }
                        }

                        if (escolha == 1) {
                            while (condicao) {
                                String email = JOptionPane.showInputDialog(null, "Digite o novo email: ");
                                if(email == null){break;}
                                int simnao = JOptionPane.showConfirmDialog(null, "Voce Digitou: " + email + " Está correto ?", "Confirmação", JOptionPane.YES_NO_OPTION);
                                if (simnao == 0) {
                                    conexao.alterar2(conn, ID, email);
                                    break;
                                }
                                if (simnao == 1) {
                                    JOptionPane.showMessageDialog(null, "Então vamos recomeçar");
                                }
                            }
                        }

                        if (escolha == 2) {
                            while (condicao) {
                                String telefone = JOptionPane.showInputDialog(null, "Digite o telefone: ");
                                if(telefone == null){break;}
                                int simnao = JOptionPane.showConfirmDialog(null, "Voce Digitou: " + telefone + " Está correto ?", "Confirmação", JOptionPane.YES_NO_OPTION);
                                if (simnao == 0) {
                                    conexao.alterar3(conn, ID, telefone);
                                    break;
                                }
                                if (simnao == 1) {
                                    JOptionPane.showMessageDialog(null, "Então vamos recomeçar");
                                }
                            }
                        }

                    }

                }

            }


        }
    }

}



