# Gerenciamento-de-pessoass
```Java
public class Pessoa {
    private String nome;
    private int idade;
    private String EstadoCivil;
    private String Data;
    private String CPF;
    private String profissao; 
    
    //Construtor
    public Pessoa(){}
    public Pessoa(String nome, int idade, String EstadoCivil, String Data, String CPF, String profissao) {
        this.nome = nome;
        this.idade = idade;
        this.EstadoCivil = EstadoCivil;
        this.Data = Data;
        this.CPF = CPF;
        this.profissao = profissao;
    }
    //Metodo toString

    @Override
    public String toString() {
        return "Pessoa{" + "nome=" + nome + ", idade=" + idade + ", EstadoCivil=" + EstadoCivil + ", Data=" + Data + ", CPF=" + CPF + ", profissao=" + profissao + '}';
    }
    

    public void setNome(String nome) {
        this.nome = nome;
    }

    public void setIdade(int idade) {
        this.idade = idade;
    }
    
    public void setEstadoCivil(String EstadoCivil){
        this.EstadoCivil = EstadoCivil;
    }

    public void setData(String Data){
        this.Data = Data;
    }

    public void setCPF(String CPF){
        this.CPF = CPF;
    }

    public void setprofissao(String profissao){
        this.profissao = profissao;
    }
    
    public String getNome(){
        return nome;
    }
    
    public int getIdade(){
        return idade;
    }
    
    public String getEstadoCivil(){
        return EstadoCivil;
    }
    
    public String getData(){
        return Data;
    }
    
    public String getCPF(){
        return CPF;
    }
    
    public String getprofissao(){
        return profissao;
    }
}

import java.util.List;

public class Principal {
    public static void main(String[] args) {
        
        Agenda agenda = new Agenda();
        Pessoa novaPessoa = new Pessoa("Carlos", 20, "Solteiro", "19/02/2003", "111.111.111-11", "Fazendeiro\n");
        System.out.println(novaPessoa.toString());

        Pessoa novaPessoa1 = new Pessoa("Bella", 20, "Casada", "09/02/2004", "222.222.222-22", "Veterinaria");
        Pessoa novaPessoa2 = new Pessoa("Anthony", 21, "Casado", "30/06/2002", "333.333.333-33", "Médico");
        Pessoa novaPessoa3 = new Pessoa("Elvis", 34, "Solteiro", "28/05/1999", "444.444.444-44", "Analista");
        
        agenda.adicionarPessoa(novaPessoa1);
        agenda.adicionarPessoa(novaPessoa2);
        agenda.adicionarPessoa(novaPessoa3);

        List<Pessoa> pessoasComProfissao = agenda.buscarPessoaPorProfissao("Analista");
        
        if(pessoasComProfissao != null) {
            System.out.println(pessoasComProfissao.toString());
        } else { 
            System.out.println("nenhuma pessoa contem essa profissão!");
        }
        System.out.println("\n" + agenda.getListadeContatos());

    }
}

import java.util.ArrayList;
import java.util.List;

public class Agenda extends Pessoa {   

        private List<Pessoa> ListadeContatos;

        public Agenda() {
            this.ListadeContatos = new ArrayList<>();
        }

        public void adicionarPessoa(Pessoa novaPessoa) {
            ListadeContatos.add(novaPessoa);
        }

        public Pessoa buscarPessoaPorNome(String nome) {

            for (Pessoa pessoa : this.ListadeContatos) {
                if (pessoa.getNome().equals(nome)) {
                    return pessoa;
                }
            }
            return null;
        }

        public List<Pessoa> buscarPessoaPorProfissao(String Profissao) {
            List<Pessoa> pessoaComProfissao = new ArrayList();

            ListadeContatos.forEach(profissional -> {
                if (profissional.getprofissao().equals(Profissao)) {
                    pessoaComProfissao.add(profissional);
                }
            });

            return pessoaComProfissao;
        }

    public List<Pessoa> getListadeContatos() {
        return ListadeContatos;
    }

    public void setListadeContatos(List<Pessoa> ListadeContatos) {
        this.ListadeContatos = ListadeContatos;
    }
}
```
