# lista4_javascript


const readline = require('readline');

const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});

// Função para calcular a média
function calcularMedia(notas) {
  const soma = notas.reduce((total, nota) => total + nota, 0);
  return soma / notas.length;
}

rl.question('Digite a primeira nota: ', (nota1) => {
  rl.question('Digite a segunda nota: ', (nota2) => {
    rl.question('Digite a terceira nota: ', (nota3) => {
      const notas = [parseFloat(nota1), parseFloat(nota2), parseFloat(nota3)];
      const media = calcularMedia(notas);

      console.log(`A média do aluno é: ${media.toFixed(2)}`);

      if (media <= 4) {
        console.log('Aluno reprovado.');
      } else if (media < 7) {
        rl.question('Digite a nota da recuperação: ', (recuperacao) => {
          const notaRecuperacao = parseFloat(recuperacao);
          const novaMedia = (media + notaRecuperacao) / 2;

          if (novaMedia >= 5) {
            console.log('Aluno aprovado na recuperação.');
          } else {
            console.log('Aluno reprovado na recuperação.');
          }

          rl.close();
        });
      } else {
        console.log('Aluno aprovado.');
        rl.close();
      }
    });
  });
});
