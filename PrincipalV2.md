```java
import java.awt.HeadlessException;
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
					String matriculaS = JOptionPane.showInputDialog("Digite a matricula do aluno");
					if(matriculaS==null || matriculaS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int matricula = Integer.parseInt(matriculaS);
					String nome = JOptionPane.showInputDialog("Digite o nome do aluno");
					if(nome==null || nome.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String semestreIngresso = JOptionPane.showInputDialog("Digite o semestre de ingresso do aluno");
					if(semestreIngresso==null || semestreIngresso.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String formaIngresso = JOptionPane.showInputDialog("Digite a forma de ingresso do aluno");
					if(formaIngresso==null || formaIngresso.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String curso = JOptionPane.showInputDialog("Digite o curso do aluno");
					if(curso==null || curso.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String provavelFormaturaS = JOptionPane.showInputDialog("Digite a provavel data de "
							+ "formatura do aluno (formato: dd/mm/aa)");
					if(provavelFormaturaS==null || provavelFormaturaS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					Date provavelFormatura = inputFormat.parse(provavelFormaturaS);
					Graduacao g = new Graduacao(matricula, nome, semestreIngresso, formaIngresso, curso, provavelFormatura);
					alunoG.add(g);
				}catch(ParseException e){
					JOptionPane.showMessageDialog(null, "formato de data incorreta (formato: dd/mm/aa)!");
					
				}catch(NumberFormatException e1){
					JOptionPane.showMessageDialog(null, "entrada não permitida");
					
				}catch(InformacaoFaltanteException e2){
					JOptionPane.showMessageDialog(null, "Informacao faltando na classe Aluno Graduacao!");
				}

				break;
			case 2:
				try{
					SimpleDateFormat inputFormat = new SimpleDateFormat("dd/mm/yy");
					String matriculaS = JOptionPane.showInputDialog("Digite a matricula do aluno");
					if(matriculaS==null || matriculaS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int matricula = Integer.parseInt(matriculaS);
					String nome = JOptionPane.showInputDialog("Digite o nome do aluno");
					if(nome==null || nome.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String semestreIngresso = JOptionPane.showInputDialog("Digite o semestre de ingresso do aluno");
					if(semestreIngresso==null || semestreIngresso.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String semestreQualificacao = JOptionPane.showInputDialog("Digite o semestre de qualificação do aluno");
					if(semestreQualificacao==null || semestreQualificacao.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String dataDefesaS = JOptionPane.showInputDialog("Digite a provavel data de formatura do aluno (formato: dd/mm/aa)");
					if(dataDefesaS==null || dataDefesaS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					Date dataDefesa = inputFormat.parse(dataDefesaS);
	
					PosGraduacao pg = new PosGraduacao(matricula, nome, semestreIngresso, semestreQualificacao, dataDefesa);
					alunoPG.add(pg);
				}catch(ParseException e){
					JOptionPane.showMessageDialog(null, "formato de data incorreta!");
				}catch(NumberFormatException e){
					JOptionPane.showMessageDialog(null, "entrada não permitida");
				}catch(InformacaoFaltanteException e2){
					JOptionPane.showMessageDialog(null, "Informacao faltando na classe Aluno Pós Graduacao!");
				}
				break;
			case 3:
				try{
					SimpleDateFormat inputFormat = new SimpleDateFormat("dd/mm/yy");
					String matriculaS = JOptionPane.showInputDialog("Digite a matricula do aluno");
					if(matriculaS==null || matriculaS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int matricula = Integer.parseInt(matriculaS);
					String nome = JOptionPane.showInputDialog("Digite o nome do aluno");
					if(nome==null || nome.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String semestreIngresso = JOptionPane.showInputDialog("Digite o semestre de ingresso do aluno");
					if(semestreIngresso==null || semestreIngresso.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String semestreQualificacao = JOptionPane.showInputDialog("Digite o semestre de qualificação do aluno");
					if(semestreQualificacao==null || semestreQualificacao.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String dataDefesaS = JOptionPane.showInputDialog("Digite a provavel data de formatura do aluno (formato: dd/mm/aa)");
					if(dataDefesaS==null || dataDefesaS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					Date dataDefesa = inputFormat.parse(dataDefesaS);
					String taxaPagaS = JOptionPane.showInputDialog("Pagou taxa? (True ou False)");
					if(taxaPagaS==null || taxaPagaS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					boolean taxaPaga = Boolean.parseBoolean(taxaPagaS);
					String semestreCursado  = JOptionPane.showInputDialog("Digite semestre cursado");
					if(semestreCursado==null || semestreCursado.isEmpty()){
						throw new InformacaoFaltanteException();
					}
	
					Especial e = new Especial(matricula, nome, semestreIngresso, semestreQualificacao, dataDefesa, taxaPaga, semestreCursado);
					alunoE.add(e);
				}catch(ParseException e){
					JOptionPane.showMessageDialog(null, "formato de data incorreta (formato: dd/mm/aa)!");
				}catch(NumberFormatException e){
					JOptionPane.showMessageDialog(null, "entrada não permitida");
				}catch(InformacaoFaltanteException e2){
					JOptionPane.showMessageDialog(null, "Informacao faltando na classe Aluno Especial!");
				}
				break; 	
			case 4:
				try{
					String matriculaSiapeS = JOptionPane.showInputDialog("Digite a matricula Siape do professor");
					if(matriculaSiapeS==null || matriculaSiapeS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int matriculaSiape = Integer.parseInt(matriculaSiapeS);
					String matriculaFUBS = JOptionPane.showInputDialog("Digite a matricula FUB do professor");
					if(matriculaFUBS==null || matriculaFUBS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int matriculaFUB = Integer.parseInt(matriculaFUBS);
					String formacao = JOptionPane.showInputDialog("Digite a formação do professor");
					if(formacao==null || formacao.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String salarioS = JOptionPane.showInputDialog("Digite o salário do professor");
					if(salarioS==null || salarioS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					float salario = Float.parseFloat(salarioS);
					String graduacao = JOptionPane.showInputDialog("Digite a graduação do professor");
					if(graduacao==null || graduacao.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String anoGraduacaoS = JOptionPane.showInputDialog("Digite o ano de graduação do professor");
					if(anoGraduacaoS==null || anoGraduacaoS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int anoGraduacao = Integer.parseInt(anoGraduacaoS);
					
					Auxiliar a = new Auxiliar(matriculaSiape, matriculaFUB, formacao, salario, graduacao, anoGraduacao);
					professorAux.add(a);	
				}catch(NumberFormatException e){
					JOptionPane.showMessageDialog(null, "entrada não permitida");
				}catch(InformacaoFaltanteException e2){
					JOptionPane.showMessageDialog(null, "Informacao faltando na classe Professor Auxiliar!");
				}
				break;
			case 5:
				try{
					String matriculaSiapeS = JOptionPane.showInputDialog("Digite a matricula Siape do professor");
					if(matriculaSiapeS==null || matriculaSiapeS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int matriculaSiape = Integer.parseInt(matriculaSiapeS);
					String matriculaFUBS = JOptionPane.showInputDialog("Digite a matricula FUB do professor");
					if(matriculaFUBS==null || matriculaFUBS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int matriculaFUB = Integer.parseInt(matriculaFUBS);
					String formacao = JOptionPane.showInputDialog("Digite a formação do professor");
					if(formacao==null || formacao.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String salarioS = JOptionPane.showInputDialog("Digite o salário do professor");
					if(salarioS==null || salarioS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					float salario = Float.parseFloat(salarioS);
					String graduacao = JOptionPane.showInputDialog("Digite a graduação do professor");
					if(graduacao==null || graduacao.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String anoGraduacaoS = JOptionPane.showInputDialog("Digite o ano de graduação do professor");
					if(anoGraduacaoS==null || anoGraduacaoS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int anoGraduacao = Integer.parseInt(anoGraduacaoS);
					String mestrado = JOptionPane.showInputDialog("Digite o mestrado do professor");
					if(mestrado==null || mestrado.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String anoMestradoS = JOptionPane.showInputDialog("Digite o ano do mestrado do professor");
					if(anoMestradoS==null || anoMestradoS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int anoMestrado = Integer.parseInt(anoMestradoS);
					String tituloDissertacao = JOptionPane.showInputDialog("Digite o título da dissertação do professor");
					if(tituloDissertacao==null || tituloDissertacao.isEmpty()){
						throw new InformacaoFaltanteException();
					}
	
					Assistente as = new Assistente(matriculaSiape, matriculaFUB, formacao, salario, graduacao, anoGraduacao, mestrado, anoMestrado, tituloDissertacao);
					professorAs.add(as);	
				}catch(NumberFormatException e){
					JOptionPane.showMessageDialog(null, "entrada não permitida");
				}catch(InformacaoFaltanteException e2){
					JOptionPane.showMessageDialog(null, "Informacao faltando na classe Professor Assistente!");
				}
				break;
			case 6:
				try{
					String matriculaSiapeS = JOptionPane.showInputDialog("Digite a matricula Siape do professor");
					if(matriculaSiapeS==null || matriculaSiapeS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int matriculaSiape = Integer.parseInt(matriculaSiapeS);
					String matriculaFUBS = JOptionPane.showInputDialog("Digite a matricula FUB do professor");
					if(matriculaFUBS==null || matriculaFUBS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int matriculaFUB = Integer.parseInt(matriculaFUBS);
					String formacao = JOptionPane.showInputDialog("Digite a formação do professor");
					if(formacao==null || formacao.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String salarioS = JOptionPane.showInputDialog("Digite o salário do professor");
					if(salarioS==null || salarioS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					float salario = Float.parseFloat(salarioS);
					String graduacao = JOptionPane.showInputDialog("Digite a graduação do professor");
					if(graduacao==null || graduacao.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String anoGraduacaoS = JOptionPane.showInputDialog("Digite o ano de graduação do professor");
					if(anoGraduacaoS==null || anoGraduacaoS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int anoGraduacao = Integer.parseInt(anoGraduacaoS);
					String mestrado = JOptionPane.showInputDialog("Digite o mestrado do professor");
					if(mestrado==null || mestrado.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String anoMestradoS = JOptionPane.showInputDialog("Digite o ano do mestrado do professor");
					if(anoMestradoS==null || anoMestradoS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int anoMestrado = Integer.parseInt(anoMestradoS);
					String tituloDissertacao = JOptionPane.showInputDialog("Digite o título da dissertação do professor");
					if(tituloDissertacao==null || tituloDissertacao.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String doutorado = JOptionPane.showInputDialog("Digite o mestrado do professor");
					if(doutorado==null || doutorado.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String anoDoutoradoS = JOptionPane.showInputDialog("Digite o ano do mestrado do professor");
					if(anoDoutoradoS==null || anoDoutoradoS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int anoDoutorado = Integer.parseInt(anoDoutoradoS);
					String tituloTese = JOptionPane.showInputDialog("Digite o título da dissertação do professor");
					if(tituloTese==null || tituloTese.isEmpty()){
						throw new InformacaoFaltanteException();
					}
	
					Adjunto adj = new Adjunto(matriculaSiape, matriculaFUB, formacao, salario, graduacao,
							anoGraduacao, mestrado, anoMestrado, tituloDissertacao, doutorado,
							anoDoutorado, tituloTese);
					professorAdj.add(adj);
				}catch(NumberFormatException e){
					JOptionPane.showMessageDialog(null, "entrada não permitida");
				}catch(InformacaoFaltanteException e2){
					JOptionPane.showMessageDialog(null, "Informacao faltando na classe Professor Adjunto!");
				}
				break;
			case 7:
				try{
					String matriculaSiapeS = JOptionPane.showInputDialog("Digite a matricula Siape do professor");
					if(matriculaSiapeS==null || matriculaSiapeS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int matriculaSiape = Integer.parseInt(matriculaSiapeS);
					String matriculaFUBS = JOptionPane.showInputDialog("Digite a matricula FUB do professor");
					if(matriculaFUBS==null || matriculaFUBS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int matriculaFUB = Integer.parseInt(matriculaFUBS);
					String formacao = JOptionPane.showInputDialog("Digite a formação do professor");
					if(formacao==null || formacao.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String salarioS = JOptionPane.showInputDialog("Digite o salário do professor");
					if(salarioS==null || salarioS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					float salario = Float.parseFloat(salarioS);
					String graduacao = JOptionPane.showInputDialog("Digite a graduação do professor");
					if(graduacao==null || graduacao.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String anoGraduacaoS = JOptionPane.showInputDialog("Digite o ano de graduação do professor");
					if(anoGraduacaoS==null || anoGraduacaoS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int anoGraduacao = Integer.parseInt(anoGraduacaoS);
					String mestrado = JOptionPane.showInputDialog("Digite o mestrado do professor");
					if(mestrado==null || mestrado.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String anoMestradoS = JOptionPane.showInputDialog("Digite o ano do mestrado do professor");
					if(anoMestradoS==null || anoMestradoS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int anoMestrado = Integer.parseInt(anoMestradoS);
					String tituloDissertacao = JOptionPane.showInputDialog("Digite o título da dissertação do professor");
					if(tituloDissertacao==null || tituloDissertacao.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String doutorado = JOptionPane.showInputDialog("Digite o mestrado do professor");
					if(doutorado==null || doutorado.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String anoDoutoradoS = JOptionPane.showInputDialog("Digite o ano do mestrado do professor");
					if(anoDoutoradoS==null || anoDoutoradoS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int anoDoutorado = Integer.parseInt(anoDoutoradoS);
					String tituloTese = JOptionPane.showInputDialog("Digite o título da dissertação do professor");
					if(tituloTese==null || tituloTese.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String areaDePesquisa = JOptionPane.showInputDialog("Digite a área de pesquisa do professor");
					if(areaDePesquisa==null || areaDePesquisa.isEmpty()){
						throw new InformacaoFaltanteException();
					}
	
					Associado asd = new Associado(matriculaSiape, matriculaFUB, formacao, salario, graduacao, anoGraduacao, 
							mestrado, anoMestrado, tituloDissertacao, doutorado, anoDoutorado, tituloTese, areaDePesquisa);
					professorAsd.add(asd);
				}catch(NumberFormatException e){
					JOptionPane.showMessageDialog(null, "entrada não permitida");
				}catch(InformacaoFaltanteException e2){
					JOptionPane.showMessageDialog(null, "Informacao faltando na classe Professor Associado!");
				}
				
				break;
			case 8:
				try{
					SimpleDateFormat inputFormat = new SimpleDateFormat("dd/mm/yy");
					String matriculaSiapeS = JOptionPane.showInputDialog("Digite a matricula Siape do professor");
					if(matriculaSiapeS==null || matriculaSiapeS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int matriculaSiape = Integer.parseInt(matriculaSiapeS);
					String matriculaFUBS = JOptionPane.showInputDialog("Digite a matricula FUB do professor");
					if(matriculaFUBS==null || matriculaFUBS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int matriculaFUB = Integer.parseInt(matriculaFUBS);
					String formacao = JOptionPane.showInputDialog("Digite a formação do professor");
					if(formacao==null || formacao.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String salarioS = JOptionPane.showInputDialog("Digite o salário do professor");
					if(salarioS==null || salarioS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					float salario = Float.parseFloat(salarioS);
					String graduacao = JOptionPane.showInputDialog("Digite a graduação do professor");
					if(graduacao==null || graduacao.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String anoGraduacaoS = JOptionPane.showInputDialog("Digite o ano de graduação do professor");
					if(anoGraduacaoS==null || anoGraduacaoS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int anoGraduacao = Integer.parseInt(anoGraduacaoS);
					String mestrado = JOptionPane.showInputDialog("Digite o mestrado do professor");
					if(mestrado==null || mestrado.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String anoMestradoS = JOptionPane.showInputDialog("Digite o ano do mestrado do professor");
					if(anoMestradoS==null || anoMestradoS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int anoMestrado = Integer.parseInt(anoMestradoS);
					String tituloDissertacao = JOptionPane.showInputDialog("Digite o título da dissertação do professor");
					if(tituloDissertacao==null || tituloDissertacao.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String doutorado = JOptionPane.showInputDialog("Digite o mestrado do professor");
					if(doutorado==null || doutorado.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String anoDoutoradoS = JOptionPane.showInputDialog("Digite o ano do mestrado do professor");
					if(anoDoutoradoS==null || anoDoutoradoS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int anoDoutorado = Integer.parseInt(anoDoutoradoS);
					String tituloTese = JOptionPane.showInputDialog("Digite o título da dissertação do professor");
					if(tituloTese==null || tituloTese.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String areaDePesquisa = JOptionPane.showInputDialog("Digite a área de pesquisa do professor");
					if(areaDePesquisa==null || areaDePesquisa.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String concursoS = JOptionPane.showInputDialog("Digite a data do concurso do professor (formato: dd/mm/aa)");
					if(concursoS==null || concursoS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					Date concurso = inputFormat.parse(concursoS);
					String dataDeAdmissaoS = JOptionPane.showInputDialog("Digite a data de admissão do professor (formato: dd/mm/aa)");
					if(dataDeAdmissaoS==null || dataDeAdmissaoS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					Date dataDeAdmissao = inputFormat.parse(dataDeAdmissaoS);
	
					Titular t = new Titular(matriculaSiape, matriculaFUB, formacao, salario, graduacao, anoGraduacao, 
							mestrado, anoMestrado, tituloDissertacao, doutorado, anoDoutorado, 
							tituloTese, areaDePesquisa, concurso, dataDeAdmissao);
					professorT.add(t);
				}catch(ParseException e){
					JOptionPane.showMessageDialog(null, "formato de data incorreta (formato: dd/mm/aa)!");
				}catch(NumberFormatException e){
					JOptionPane.showMessageDialog(null, "entrada não permitida");
				}catch(InformacaoFaltanteException e2){
					JOptionPane.showMessageDialog(null, "Informacao faltando na classe Professor Titular!");
				}

				break;
			case 9:
				try{
					String nome = JOptionPane.showInputDialog("Digite o nome da disciplina");
					if(nome==null || nome.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String cargaHorariaS = JOptionPane.showInputDialog("Digite a carga horária da disciplina");
					if(cargaHorariaS==null || cargaHorariaS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int cargaHoraria = Integer.parseInt(cargaHorariaS);
					
					Disciplina d = new Disciplina(nome, cargaHoraria);
					disc.add(d);
				}catch(NumberFormatException e){
					JOptionPane.showMessageDialog(null, "entrada não permitida");
				}catch(InformacaoFaltanteException e2){
					JOptionPane.showMessageDialog(null, "Informacao faltando na classe Disciplina!");
				}
				break;
			case 10:
				try{
					String nome = JOptionPane.showInputDialog("Digite o nome do estágio");
					if(nome==null || nome.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String cargaHorariaS = JOptionPane.showInputDialog("Digite a carga horária do estágio");
					if(cargaHorariaS==null || cargaHorariaS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int cargaHoraria = Integer.parseInt(cargaHorariaS);
					String localDeEstagio = JOptionPane.showInputDialog("Digite o local do estágio");
					if(localDeEstagio==null || localDeEstagio.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					String responsavel = JOptionPane.showInputDialog("Digite o nome do responsável pelo estágio");
					if(responsavel==null || responsavel.isEmpty()){
						throw new InformacaoFaltanteException();
					}
	
					Estagio es = new Estagio(nome, cargaHoraria, localDeEstagio, responsavel);
					est.add(es);
				}catch(NumberFormatException e){
					JOptionPane.showMessageDialog(null, "entrada não permitida");
				}catch(InformacaoFaltanteException e2){
					JOptionPane.showMessageDialog(null, "Informacao faltando na classe Estágio!");
				}
				break;
			case 11:
				try{
					String codigoS = JOptionPane.showInputDialog("Digite o código da turma");
					if(codigoS==null || codigoS.isEmpty()){
						throw new InformacaoFaltanteException();
					}
					int codigo = Integer.parseInt(codigoS);
					String horario = JOptionPane.showInputDialog("Digite o horário da turma");
					if(horario==null || horario.isEmpty()){
						throw new InformacaoFaltanteException();
					}
	
					Turma tu = new Turma(codigo, horario);
					tur.add(tu);
				}catch(NumberFormatException e){
					JOptionPane.showMessageDialog(null, "entrada não permitida");
				}catch(InformacaoFaltanteException e2){
					JOptionPane.showMessageDialog(null, "Informacao faltando na classe Turma!");
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
