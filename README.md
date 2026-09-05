## ⚙️ Otimização de Hiperparâmetros (Optuna)

A busca foi conduzida ao longo de **30 trials** (`n_trials=30`) para maximizar o desempenho no conjunto de validação.

### 🏆 Melhores Hiperparâmetros Encontrados

| Hiperparâmetro | Parâmetro no Código | Valor Otimizado |
| :--- | :--- | :--- |
| **Acurácia de Validação** | `val_accuracy` | **0.9775 (~97.75%)** |
| **Camadas Ocultas** | `n_layers` | `1` |
| **Unidades (Camada 0)** | `units_l0` | `64` |
| **Taxa de Aprendizado** | `learning_rate` | `0.001354` |
| **Taxa de Dropout** | `drop_rate` | `0.1769` |
| **Tamanho do Lote** | `batch_size` | `128` |

---

## 📊 Desempenho e Avaliação do Modelo

O modelo treinado com a melhor configuração alcançou **97.54% de acurácia** no conjunto de teste (`MNIST`), demonstrando alta consistência e capacidade de generalização para dígitos não vistos.

### Diagnóstico de Qualidade

* **Generalização vs. Overfitting:** A proximidade entre a acurácia de validação (**97.75%**) e a de teste (**97.54%**) evidencia ausência de overfitting crítico. A taxa de *Dropout* de ~0.177 atuou como regularizador suficiente sem degradar a convergência.
* **Complexidade Arquitetural:** O algoritmo convergiu para uma topologia enxuta (1 camada oculta com 64 neurônios). Essa estrutura reduz o custo computacional por época e minimiza a variância excessiva.
* **Estabilidade do Treinamento:** A combinação de `batch_size=128` com `learning_rate ≈ 1.35e-3` garantiu passos de gradiente estáveis, evitando oscilações acentuadas na função de perda (*loss*).

> **Conclusão:** O pipeline com Optuna encontrou uma arquitetura compacta, rápida de treinar e com alta taxa de acerto para a tarefa proposta, equilibrando capacidade expressiva e regularização.
