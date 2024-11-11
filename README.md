# Analisando a parte 3 da prática de orientação a objetos  
## João Antonio B. Lobler
## Sistemas de Informação

### Análise do diagrama de classes:
![image](https://github.com/user-attachments/assets/5d309f41-897d-426b-a72f-e339c38a2116)

Analisando rapidamente é possível perceber que o diagrama nos apresenta um sistema definido em 3 classes com atributos e métodos definidos, sendo elas as classes de:
* Student
* Professor
* Group
  
Sendo a última classe citada a que se relaciona com as 2 primeiras como indicado pelo "has-a"

### Completando o código

O exercício pedia que fosse completado dois métodos que estavam definidos na classe `group`

Primeramente o método `userExists` 
~~~
public boolean userExists(String userId) {
    // COMPLETE-ME
    // Verifique se existe o userId na lista de estudantes ou de professores
    // Veja no método anterior como percorrer as listas de estudantes e professores

  }
~~~

E seguidamente o método `countMembers`
~~~
public int countMembers() {
    // COMPLETE-ME
    // Retorne o total de membros do grupo (estudantes e professores)
    // Para isso, descubra qual método chamar para obter o tamanho de um ArrayList
  }
~~~

Completando primeiramente o método `userExists`, implementar ele foi bem simples:

~~~
public boolean userExists(String userId) {

        for (Student student : students) {
            if (student.getUserId().equals(userId)) {
                return true;
            }
        }

        for (Professor professor : professors) {
            if (professor.getUserId().equals(userId)) {
                return true;
            }
        }
        
        return false;

    }
~~~

Um método que foi implementado da seguinte forma ele percorre a lista de alunos ou de professores e então em cada uma das iterações ele verifica a condição, é chamado o método `getUserId` (que é publico) para
decobrir qual id esta relacionado à aquele estudante/professor e o `equals` faz como que ele seja comparado com o `userId` passado como paramêtro, caso seja verdadeiro retorna `true` caso não esteja na lista retorna `false`.

Para implementar o método countMembers não foi complicado também, o método `.size` retorna o tamanho de um array em java dessa forma como o método serve para retornar a quantidade total de pessoas no grupo o código fica dessa forma:

~~~
public int countMembers() {
        
        return students.size() + professors.size();
    }
~~~




### Referências:

* https://www.dio.me/articles/o-uso-do-arraylist-em-java
* https://www.dio.me/articles/equals-em-java-compreendendo-e-implementando-a-comparacao-de-objetos


