# Projeto_Elevador_Oceanlab
Funcionamento do projeto Elevador

Primeiramente a Classe Elevador foi criada, dentro da pasta Model.

A Classe Elevador contém as variáveis para determinar a Capacidade do elevador, o Total de Andares, e os andares que o usuário gostaria de ir e onde ele se encontra. 
Basicamente armazenando todas as propriedades do Elevador na própria Classe e também armazenando as funcoes para o funcionamento do Elevador.

O primeiro passo no funcionamento do Elevador é o instanciamento da classe elevador, para conseguir disponibiliza-la na memoria. 
Feito com o comando : 

Model.Elevador elevador = new Model.Elevador(); //na linha 16 no arquivo Program.cs

Depois de instanciada a classe, é necessário atribuir algumas propriedades. Neste caso, os valores que precisam ser fixados sao os seguintes:

            elevador.Id = 1;
            elevador.Capacidade = 4;
            elevador.TotalAndar = 8;
            elevador.andarterreo = 0;

            // Favor comunicar aqui o Andar Atual e o Andar Desejado ANTES de iniciar o programa com CTRL F5.

            elevador.andaratual = 2; // andar que o usuario se encontra atualmente
            elevador.andardesejado = 5; // andar que o usuario deseja ir

O usuário do elevador deve preencher os seguintes detalhes ANTES de comecar usar o programa
Apos deixar os valores fixos, o usuario pode comecar interagir com o sistema.

Foi criado um menu para que o usuario informe a quantidade de pessoas entrando no elevador. Também para que o usuario comunique para qual andar ele deseja ir Foram criadas 6 funcoes no total, as 5 que sao requisito do projeto + 2 funcoes de erro caso o usuario digitasse um andar nao disponivel ou superasse a capacidade maxima de pessoas permitidas no elevador. 
// O menu foi feito dentro de um loop do while.

            do
            {
                Console.WriteLine(@"Olá! Bem-vindo ao elevador {0}, 
favor selecionar o andar atual, o andar desejado e a quantidade de pessoas entrando ", elevador.Id);

                elevador.andardatual = int.Parse(Console.ReadLine());
                elevador.andardesejado = int.Parse(Console.ReadLine());
                entrando = int.Parse(Console.ReadLine());

                // Precisa converter a resposta do usuario para int


                if (entrando > elevador.Capacidade)
                {
                    Elevador.Error();
                }
                else if (elevador.andardesejado > elevador.TotalAndar)
                {
                    Elevador.Error2();
                }
                else
                // Aqui comeca o loop para decidir se o usuario sobe ou desce no elevador, com as respetivas funcoes.
                
                {
                    Elevador.Inicializar();
                    if (elevador.andardatual != elevador.andarterreo)
                    {
                        Console.WriteLine(@"Elevador chegando até você");
                        Console.WriteLine(@"O elevador se encontra no andar {0}", elevador.andarterreo);

                        Console.WriteLine(@"O elevador está indo para o andar {0}", elevador.andardatual);

                        Elevador.Entrar();
                        elevador.andarterreo = elevador.andaratual;

                        if (elevador.andardatual > elevador.andardesejado)
                        {
                            Elevador.Descer();

                        } else { Elevador.Subir(); }

                        Elevador.Sair();
                        


                    }
                    else
                    {
                        Elevador.Entrar();
                        if(elevador.andardatual > elevador.andardesejado)
                        {
                            Elevador.Descer();

                        } else { Elevador.Subir(); }
                        Elevador.Sair();
                    }

                }
            }
            while (continuar);


        }

    }
}

As funcoes sao as seguintes: 


        public static void Inicializar()
        {      
            Console.WriteLine(@"Chamando o Elevador!");
            
        }
        public static void Error()
        {
            Console.WriteLine("A capacidade máxima do elevador foi superada");
        }

        internal static void Error2()
        {
            Console.WriteLine("Digite um andar válido"); 
             
        }

        internal static void Entrar()
        {
            Console.WriteLine("Favor entrar!");
        }

      

        internal static void Descer()
        {
            Console.WriteLine("Estamos descendo!");
        }

        internal static void Subir()
        {
            Console.WriteLine("Estamos Subindo!");
        }

        internal static void Sair()
        {
            Console.WriteLine("Chegamos! Favor sair!");
        }
    }
}

