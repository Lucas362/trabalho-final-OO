Man, isso é o q eu fiz até agora

```java
import java.awt.HeadlessException;
import java.io.BufferedWriter;
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.LinkedList;
import java.util.List;

import javax.swing.JOptionPane;

public class Principal {

	public static void main(String[] args) throws HeadlessException, ParseException{

		int op = 1;
		
		List<Graduacao> alunoG;
		alunoG = new LinkedList<Graduacao>();
		
		List<PosGraduacao> alunoPG;
		alunoPG = new LinkedList<PosGraduacao>();
		
		List<Especial> alunoE;
		alunoE = new LinkedList<Especial>();
		
		List<Auxiliar> professorAux;
		professorAux = new LinkedList<Auxiliar>();
		
		List<Assistente> professorAs;
		professorAs = new LinkedList<Assistente>();
		
		List<Adjunto> professorAdj;
		professorAdj = new LinkedList<Adjunto>();
		
		List<Associado> professorAsd;
		professorAsd = new LinkedList<Associado>();
		
		List<Titular> professorT;
		professorT = new LinkedList<Titular>();
		
		List<Disciplina> disc;
		disc = new LinkedList<Disciplina>();
		
		List<Estagio> est;
		est = new LinkedList<Estagio>();
		
		List<Turma> tur;
		tur = new LinkedList<Turma>();

		while(op!=0){
			try{
				String result = JOptionPane.showInputDialog("----Digite uma das opções abaixo----\n\n"
						+ " 1 - Cadastrar aluno de graduação\n"
						+ " 2 - Cadastrar aluno de pos-graduação\n"
						+ " 3 - Cadastrar aluno especial\n"
						+ " 4 - Cadastrar professor auxiliar\n"
						+ " 5 - Cadastrar professor assistente\n"
						+ " 6 - Cadastrar professor adjunto\n"
						+ " 7 - Cadastrar professor associado\n"
						+ " 8 - Cadastrar professor titular\n"
						+ " 9 - Cadastrar Disciplina\n"
						+ "10 - Cadastrar Estágio\n"
						+ "11 - Cadastrar Turma\n"
						+ " 0 - Sair");
				if(result == null){
					op = 0;
				}else{
					op = Integer.parseInt(result);
				}
			}catch (NumberFormatException e) {
				JOptionPane.showMessageDialog(null, "Digite somente números");
				op = 20;
			}
			switch(op){
			case 1:
				try{
					SimpleDateFormat inputFormat = new SimpleDateFormat("dd/mm/yy");
					int matricula = Integer.parseInt(JOptionPane.showInputDialog("Digite a matricula do aluno"));
					String nome = JOptionPane.showInputDialog("Digite o nome do aluno");
					String semestreIngresso = JOptionPane.showInputDialog("Digite o semestre de ingresso do aluno");
					String formaIngresso = JOptionPane.showInputDialog("Digite a forma de ingresso do aluno");
					String curso = JOptionPane.showInputDialog("Digite o curso do aluno");
					Date provavelFormatura = inputFormat.parse(JOptionPane.showInputDialog("Digite a provavel data de "
							+ "formatura do aluno (formato: mm/dd/yy)"));
					Graduacao g = new Graduacao(matricula, nome, semestreIngresso, formaIngresso, curso, provavelFormatura);
					alunoG.add(g);
				}catch(ParseException e){
					JOptionPane.showMessageDialog(null, "formato de data incorreta!");
				}catch(NumberFormatException e){
					JOptionPane.showMessageDialog(null, "entrada não permitida");
				}				

				break;
			case 2:
				try{
					SimpleDateFormat inputFormat = new SimpleDateFormat("MM/dd/yy");
					int matricula = Integer.parseInt(JOptionPane.showInputDialog("Digite a matricula do aluno"));
					String nome = JOptionPane.showInputDialog("Digite o nome do aluno");
					String semestreIngresso = JOptionPane.showInputDialog("Digite o semestre de ingresso do aluno");
					String semestreQualificacao = JOptionPane.showInputDialog("Digite o semestre de qualificação do aluno");
					Date dataDefesa = inputFormat.parse(JOptionPane.showInputDialog("Digite a provavel data de formatura do aluno"));
	
					PosGraduacao pg = new PosGraduacao(matricula, nome, semestreIngresso, semestreQualificacao, dataDefesa);
					alunoPG.add(pg);
				}catch(ParseException e){
					JOptionPane.showMessageDialog(null, "formato de data incorreta!");
				}catch(NumberFormatException e){
					JOptionPane.showMessageDialog(null, "entrada não permitida");
				}
				break;
			case 3:
				try{
					SimpleDateFormat inputFormat = new SimpleDateFormat("MM/dd/yy");
					int matricula = Integer.parseInt(JOptionPane.showInputDialog("Digite a matricula do aluno"));
					String nome = JOptionPane.showInputDialog("Digite o nome do aluno");
					String semestreIngresso = JOptionPane.showInputDialog("Digite o semestre de ingresso do aluno");
					String semestreQualificacao = JOptionPane.showInputDialog("Digite o semestre de qualificação do aluno");
					Date dataDefesa = inputFormat.parse(JOptionPane.showInputDialog("Digite a provavel data de formatura do aluno"));
					boolean taxaPaga = Boolean.parseBoolean(JOptionPane.showInputDialog("Pagou taxa? (True ou False)"));
					String semestreCursado  = JOptionPane.showInputDialog("Digite semestre cursado");
	
					Especial e = new Especial(matricula, nome, semestreIngresso, semestreQualificacao, dataDefesa, taxaPaga, semestreCursado);
					alunoE.add(e);
				}catch(ParseException e){
					JOptionPane.showMessageDialog(null, "formato de data incorreta!");
				}catch(NumberFormatException e){
					JOptionPane.showMessageDialog(null, "entrada não permitida");
				}
				break; 	
			case 4:
				try{
				int matriculaSiape = Integer.parseInt(JOptionPane.showInputDialog("Digite a matricula Siape do professor"));
				int matriculaFUB = Integer.parseInt(JOptionPane.showInputDialog("Digite a matricula FUB do professor"));
				String formacao = JOptionPane.showInputDialog("Digite a formação do professor");
				float salario = Float.parseFloat(JOptionPane.showInputDialog("Digite o salário do professor"));
				String graduacao = JOptionPane.showInputDialog("Digite a graduação do professor");
				int anoGraduacao = Integer.parseInt(JOptionPane.showInputDialog("Digite o ano de graduação do professor"));

				Auxiliar a = new Auxiliar(matriculaSiape, matriculaFUB, formacao, salario, graduacao, anoGraduacao);
				professorAux.add(a);	
				}catch(NumberFormatException e){
					JOptionPane.showMessageDialog(null, "entrada não permitida");
				}
				break;
			case 5:
				try{
					int matriculaSiape = Integer.parseInt(JOptionPane.showInputDialog("Digite a matricula Siape do professor"));
					int matriculaFUB = Integer.parseInt(JOptionPane.showInputDialog("Digite a matricula FUB do professor"));
					String formacao = JOptionPane.showInputDialog("Digite a formação do professor");
					float salario = Float.parseFloat(JOptionPane.showInputDialog("Digite o salário do professor"));
					String graduacao = JOptionPane.showInputDialog("Digite a graduação do professor");
					int anoGraduacao = Integer.parseInt(JOptionPane.showInputDialog("Digite o ano de graduação do professor"));
					String mestrado = JOptionPane.showInputDialog("Digite o mestrado do professor");
					int anoMestrado = Integer.parseInt(JOptionPane.showInputDialog("Digite o ano do mestrado do professor"));
					String tituloDissertacao = JOptionPane.showInputDialog("Digite o título da dissertação do professor");
	
					Assistente as = new Assistente(matriculaSiape, matriculaFUB, formacao, salario, graduacao, anoGraduacao, mestrado, anoMestrado, tituloDissertacao);
					professorAs.add(as);	
				}catch(NumberFormatException e){
					JOptionPane.showMessageDialog(null, "entrada não permitida");
				}
				break;
			case 6:
				try{
					int matriculaSiape = Integer.parseInt(JOptionPane.showInputDialog("Digite a matricula Siape do professor"));
					int matriculaFUB = Integer.parseInt(JOptionPane.showInputDialog("Digite a matricula FUB do professor"));
					String formacao = JOptionPane.showInputDialog("Digite a formação do professor");
					float salario = Float.parseFloat(JOptionPane.showInputDialog("Digite o salário do professor"));
					String graduacao = JOptionPane.showInputDialog("Digite a graduação do professor");
					int anoGraduacao = Integer.parseInt(JOptionPane.showInputDialog("Digite o ano de graduação do professor"));
					String mestrado = JOptionPane.showInputDialog("Digite o mestrado do professor");
					int anoMestrado = Integer.parseInt(JOptionPane.showInputDialog("Digite o ano do mestrado do professor"));
					String tituloDissertacao = JOptionPane.showInputDialog("Digite o título da dissertação do professor");
					String doutorado = JOptionPane.showInputDialog("Digite o doutorado do professor");
					int anoDoutorado = Integer.parseInt(JOptionPane.showInputDialog("Digite o ano do doutorado do professor"));
					String tituloTese = JOptionPane.showInputDialog("Digite o título da tese do professor");
	
					Adjunto adj = new Adjunto(matriculaSiape, matriculaFUB, formacao, salario, graduacao,
							anoGraduacao, mestrado, anoMestrado, tituloDissertacao, doutorado,
							anoDoutorado, tituloTese);
					professorAdj.add(adj);
				}catch(NumberFormatException e){
					JOptionPane.showMessageDialog(null, "entrada não permitida");
				}
				break;
			case 7:
				try{
					int matriculaSiape = Integer.parseInt(JOptionPane.showInputDialog("Digite a matricula Siape do professor"));
					int matriculaFUB = Integer.parseInt(JOptionPane.showInputDialog("Digite a matricula FUB do professor"));
					String formacao = JOptionPane.showInputDialog("Digite a formação do professor");
					float salario = Float.parseFloat(JOptionPane.showInputDialog("Digite o salário do professor"));
					String graduacao = JOptionPane.showInputDialog("Digite a graduação do professor");
					int anoGraduacao = Integer.parseInt(JOptionPane.showInputDialog("Digite o ano de graduação do professor"));
					String mestrado = JOptionPane.showInputDialog("Digite o mestrado do professor");
					int anoMestrado = Integer.parseInt(JOptionPane.showInputDialog("Digite o ano do mestrado do professor"));
					String tituloDissertacao = JOptionPane.showInputDialog("Digite o título da dissertação do professor");
					String doutorado = JOptionPane.showInputDialog("Digite o doutorado do professor");
					int anoDoutorado = Integer.parseInt(JOptionPane.showInputDialog("Digite o ano do doutorado do professor"));
					String tituloTese = JOptionPane.showInputDialog("Digite o título da tese do professor");
					String areaDePesquisa = JOptionPane.showInputDialog("Digite a área de pesquisa do professor");
	
					Associado asd = new Associado(matriculaSiape, matriculaFUB, formacao, salario, graduacao, anoGraduacao, 
							mestrado, anoMestrado, tituloDissertacao, doutorado, anoDoutorado, tituloTese, areaDePesquisa);
					professorAsd.add(asd);
				}catch(NumberFormatException e){
					JOptionPane.showMessageDialog(null, "entrada não permitida");
				}
				
				break;
			case 8:
				try{
					SimpleDateFormat inputFormat = new SimpleDateFormat("MM/dd/yy");
					int matriculaSiape = Integer.parseInt(JOptionPane.showInputDialog("Digite a matricula Siape do professor"));
					int matriculaFUB = Integer.parseInt(JOptionPane.showInputDialog("Digite a matricula FUB do professor"));
					String formacao = JOptionPane.showInputDialog("Digite a formação do professor");
					float salario = Float.parseFloat(JOptionPane.showInputDialog("Digite o salário do professor"));
					String graduacao = JOptionPane.showInputDialog("Digite a graduação do professor");
					int anoGraduacao = Integer.parseInt(JOptionPane.showInputDialog("Digite o ano de graduação do professor"));
					String mestrado = JOptionPane.showInputDialog("Digite o mestrado do professor");
					int anoMestrado = Integer.parseInt(JOptionPane.showInputDialog("Digite o ano do mestrado do professor"));
					String tituloDissertacao = JOptionPane.showInputDialog("Digite o título da dissertação do professor");
					String doutorado = JOptionPane.showInputDialog("Digite o doutorado do professor");
					int anoDoutorado = Integer.parseInt(JOptionPane.showInputDialog("Digite o ano do doutorado do professor"));
					String tituloTese = JOptionPane.showInputDialog("Digite o título da tese do professor");
					String areaDePesquisa = JOptionPane.showInputDialog("Digite a área de pesquisa do professor");
					Date concurso = inputFormat.parse(JOptionPane.showInputDialog("Digite a data do concurso do professor"));
					Date dataDeAdmissao = inputFormat.parse(JOptionPane.showInputDialog("Digite a data de admissão do professor"));;
	
	
					Titular t = new Titular(matriculaSiape, matriculaFUB, formacao, salario, graduacao, anoGraduacao, 
							mestrado, anoMestrado, tituloDissertacao, doutorado, anoDoutorado, 
							tituloTese, areaDePesquisa, concurso, dataDeAdmissao);
					professorT.add(t);
				}catch(ParseException e){
					JOptionPane.showMessageDialog(null, "formato de data incorreta!");
				}catch(NumberFormatException e){
					JOptionPane.showMessageDialog(null, "entrada não permitida");
				}

				break;
			case 9:
				try{
					String nome = JOptionPane.showInputDialog("Digite o nome da disciplina");
					int cargaHoraria = Integer.parseInt(JOptionPane.showInputDialog("Digite a carga horária da disciplina"));
	
					Disciplina d = new Disciplina(nome, cargaHoraria);
					disc.add(d);
				}catch(NumberFormatException e){
					JOptionPane.showMessageDialog(null, "entrada não permitida");
				}
				break;
			case 10:
				try{
					String nome = JOptionPane.showInputDialog("Digite o nome do estágio");
					int cargaHoraria = Integer.parseInt(JOptionPane.showInputDialog("Digite a carga horária do estágio"));
					String localDeEstagio = JOptionPane.showInputDialog("Digite o local do estágio");
					String responsavel = JOptionPane.showInputDialog("Digite o nome do responsável pelo estágio");
	
					Estagio es = new Estagio(nome, cargaHoraria, localDeEstagio, responsavel);
					est.add(es);
				}catch(NumberFormatException e){
					JOptionPane.showMessageDialog(null, "entrada não permitida");
				}
				break;
			case 11:
				try{
					int codigo = Integer.parseInt(JOptionPane.showInputDialog("Digite o código da turma"));
					String horario = JOptionPane.showInputDialog("Digite o horário da turma");
	
					Turma tu = new Turma(codigo, horario);
					tur.add(tu);
				}catch(NumberFormatException e){
					JOptionPane.showMessageDialog(null, "entrada não permitida");
				}
				break;
			case 0:
				break;
			default:
				JOptionPane.showMessageDialog(null, "Opção inválida!");

			}
		}

	}
}


```
