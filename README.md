# Statistics


## Sumário

- [📊 Imputação de Dados com KDE e Inversa da CDF](#-imputação-de-dados-com-kde-e-inversa-da-cdf-sample-from-distributionipynb)

---

## [📊 Imputação de Dados com KDE e Inversa da CDF](#-imputação-de-dados-com-kde-e-inversa-da-cdf-sample-from-distributionipynb)


Este estudo explora uma abordagem estatística para imputação de dados faltantes baseada na **estimação de densidade por núcleos (KDE)** e na **inversa da função de distribuição acumulada (CDF)**.

### Ideia Central

Em vez de preencher valores faltantes com média, mediana ou KNN, usamos a **distribuição empírica estimada** para amostrar novos valores que respeitem a **forma da distribuição original**, mantendo:

- Valor esperado (média)
- Variância
- Forma da distribuição

### Etapas

1. **Estimamos a PDF** dos dados usando `gaussian_kde`.
2. **Calculamos a CDF** integrando a KDE numericamente.
3. **Construímos a inversa da CDF** (`quantile function`) via interpolação.
4. Para cada valor faltante, **amostramos** um `u ~ U(0,1)` e usamos `inv_cdf(u)` para gerar o valor imputado.

### Avaliação

- Comparação entre os valores imputados e os originais (removidos) foi feita com:
  - Média e desvio padrão
  - Teste de Kolmogorov-Smirnov
  - Comparação visual das distribuições

O objetivo **não era recuperar os valores exatos**, mas sim **reproduzir a distribuição original dos dados** com fidelidade estatística.
![image](https://github.com/user-attachments/assets/316c12cd-6d2d-467a-a4ed-d50dc07ea822)
