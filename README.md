Aqui está o README para o jogo de carro inspirado no Rocket League:

---

# Rocket Car Game

**Descrição do Jogo:**

Rocket Car Game é um jogo de corrida e futebol inspirado no famoso Rocket League. Nele, os jogadores controlam carros em uma arena interativa, tentando marcar gols e realizar manobras acrobáticas. O jogo é altamente dinâmico, proporcionando uma experiência emocionante e competitiva.

**Instruções para Jogabilidade:**

- **Movimentação:** Use as teclas W, A, S, D para controlar o carro.
- **Pular:** Pressione a tecla Espaço para pular.
- **Boost:** Pressione Shift para ativar o turbo.
- **Controle da Câmera:** Use o mouse para ajustar a câmera.
- **Interação com a Bola:** Aproximar-se da bola para empurrá-la em direção ao gol adversário.

---

**Gameplay:**

Confira um vídeo de gameplay do jogo:

https://streamable.com/54ke95

---

**Prints de Tela:**

**Interação com a Bola:**

![Interação com a Bola](prints/interacao(batendo%20em%20bola).png)

**Interação com Rampas:**

![Interação com Rampas](prints/interacao(fisica%20de%20rampar).png)

**Passando em Lombadas:**

![Passando em Lombadas](prints/interacao(passando%20em%20lombada).png)

**Troca de Chão (Inclinado para Reto):**

![Troca de Chão](prints/interacao(troca%20de%20chão%2C%20inclinado%20para%20reto).png)

---

**Funcionalidades Desenvolvidas:**

1. **Interação com a Bola:**
   Implementamos uma funcionalidade de interação com a bola que permite ao jogador empurrá-la, proporcionando uma dinâmica de jogo similar ao futebol.

   **Código da Interação com a Bola:**
   ```csharp
   private void OnCollisionEnter(Collision collision)
   {
       if (collision.gameObject.CompareTag("Bola"))
       {
           Rigidbody bolaRigidbody = collision.gameObject.GetComponent<Rigidbody>();
           Vector3 direcao = collision.contacts[0].point - transform.position;
           direcao = direcao.normalized;
           bolaRigidbody.AddForce(direcao * forçaDoEmpurrão);
       }
   }
   ```

   **Print da Interação com a Bola:**

   ![Interação com a Bola](prints/interacao(batendo%20em%20bola).png)

2. **Interação com Rampas:**
   A física de rampas foi implementada para permitir que os carros realizem manobras acrobáticas, saltando e girando no ar.

   **Código da Interação com Rampas:**
   ```csharp
   private void OnTriggerEnter(Collider other)
   {
       if (other.CompareTag("Rampa"))
       {
           Saltar();
       }
   }

   private void Saltar()
   {
       // Código para realizar o salto na rampa
       _carRigidbody.AddForce(Vector3.up * forçaDoSalto, ForceMode.Impulse);
   }
   ```

   **Print da Interação com Rampas:**

   ![Interação com Rampas](prints/interacao(fisica%20de%20rampar).png)

3. **Passando em Lombadas:**
   Implementamos uma funcionalidade de interação com lombadas que cria uma dinâmica realista de desaceleração e aumento de dificuldade, proporcionando uma experiência de corrida mais desafiadora.

   **Código da Interação com Lombadas:**
   ```csharp
   private void OnTriggerEnter(Collider other)
   {
       if (other.CompareTag("Lombada"))
       {
           Desacelerar();
       }
   }

   private void Desacelerar()
   {
       // Código para desacelerar ao passar por lombada
       _carRigidbody.velocity *= 0.5f;
   }
   ```

   **Print da Interação com Lombadas:**

   ![Passando em Lombadas](prints/interacao(passando%20em%20lombada).png)

4. **Troca de Chão (Inclinado para Reto):**
   A transição entre diferentes tipos de terrenos foi implementada para adicionar uma camada extra de estratégia e desafio ao jogo.

   **Código da Troca de Chão:**
   ```csharp
   private void OnCollisionEnter(Collision collision)
   {
       if (collision.gameObject.CompareTag("TerrenoInclinado"))
       {
           AjustarFísicaParaTerrenoInclinado();
       }
       else if (collision.gameObject.CompareTag("TerrenoReto"))
       {
           AjustarFísicaParaTerrenoReto();
       }
   }

   private void AjustarFísicaParaTerrenoInclinado()
   {
       // Ajustes na física para terreno inclinado
       _carRigidbody.drag = dragInclinado;
   }

   private void AjustarFísicaParaTerrenoReto()
   {
       // Ajustes na física para terreno reto
       _carRigidbody.drag = dragReto;
   }
   ```

   **Print da Troca de Chão:**

   ![Troca de Chão](prints/interacao(troca%20de%20chão%2C%20inclinado%20para%20reto).png)
