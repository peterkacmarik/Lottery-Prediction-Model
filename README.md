# Lottery Prediction Model

Tento projekt sa zaoberá predikciou výherných čísel v lotérii na základe historických údajov. Na predikciu je použitý regresný model neurónovej siete implementovaný v PyTorch. Cieľom je predpovedať pravdepodobné výherné čísla a výsledné pravdepodobnosti pomocou normalizovaných údajov o výherných číslach z minulých lotérií.

## Obsah
- [Požiadavky](#požiadavky)
- [Použité knižnice](#použité-knižnice)
- [Štruktúra dát](#štruktúra-dát)
- [Model](#model)
- [Tréning](#trening)
- [Vyhodnotenie](#vyhodnotenie)
- [Inštrukcie na spustenie](#inštrukcie-na-spustenie)

## Požiadavky

Pre spustenie tohto projektu je potrebné mať nainštalované nasledovné knižnice:

- Python 3.x
- PyTorch
- Pandas
- Scikit-learn
- Matplotlib

Knižnice je možné nainštalovať pomocou príkazu:

```bash
pip install torch pandas scikit-learn matplotlib
```

## Použité knižnice

- **PyTorch**: Pre tvorbu a tréning modelu neurónovej siete.
- **Pandas**: Na spracovanie dát a manipuláciu s dátovými rámcami.
- **Scikit-learn**: Na normalizáciu dát (MinMaxScaler), rozdelenie dát na tréningovú a testovaciu sadu (train_test_split) a vyhodnotenie metriky R-squared.
- **Matplotlib**: Pre vizualizáciu tréningového procesu.

## Štruktúra dát

Dáta sú načítané zo súboru CSV s názvom `win_num.csv`. Dátový súbor obsahuje informácie o výherných číslach lotérie. Vstupné dáta zahŕňajú stĺpce ako:

- Rok, mesiac, deň
- Čísla z 1 a 2 tahu: "one_move" a "two_move"
- `final_six_figure_odds`: Koncové šestčíslie šance

Cieľom je predpovedať pravdepodobnosti a výherné čísla 1 a 2 tahu a sestciferne cislo.

## Model

Model je jednoduchá neurónová sieť definovaná v triede `LotteryModel`. Obsahuje:

- **Vstupnú vrstvu**: lineárna vrstva s 18 vstupmi
- **Batch Normalization**: pre rýchlejší a stabilnejší tréning
- **Dropout**: s pravdepodobnosťou 0.1, aby sa predišlo pretrénovaniu
- **Aktivačná funkcia Leaky ReLU**
- **Skrytá vrstva** s 10 neurónmi a výstupná vrstva s 15 výstupmi

Model predikuje viacero čísel naraz na základe historických vstupov.

## Tréning

Tréning modelu prebieha pomocou optimalizátora Adam a stratovej funkcie Mean Squared Error (MSE). Použitá je technika **early stopping**, ktorá zastaví tréning, ak sa strata na validačnej sade nezlepšuje po určitom počte epoch (v tomto prípade 10).

Model je trénovaný s týmito metrikami:

- **MAE (Mean Absolute Error)**: priemerná absolútna chyba
- **RMSE (Root Mean Squared Error)**: koreň priemernej kvadratickej chyby
- **R-squared**: koeficient determinácie, ktorý vyjadruje, ako dobre model vysvetľuje variabilitu v dátach.

## Vyhodnotenie

Počas tréningu sú metriky MAE a RMSE vypočítavané pre tréningovú aj validačnú sadu. Model tiež vyhodnocuje **R-squared** na validačných dátach. Výsledky sú vizualizované pomocou grafov.

Tréningové výsledky sú zobrazené v grafoch:

- Tréningová a validačná strata
- Tréningové a validačné MAE
- R-squared hodnoty pre validačnú sadu
- Vývoj MAE a RMSE počas epoch

## Inštrukcie na spustenie

1. Naklonuj tento repozitár na svoje lokálne zariadenie:
   ```bash
   git clone https://github.com/tvoj-repozitar/lottery-prediction.git
   cd lottery-prediction
   ```

2. Uisti sa, že máš nainštalované potrebné knižnice. Môžeš ich nainštalovať pomocou `requirements.txt` (ak je priložený):
   ```bash
   pip install -r requirements.txt
   ```

3. Ulož súbor `win_num.csv` s historickými dátami o lotérii do rovnakej zložky, kde je uložený kód.

4. Spusti tréning modelu:
   ```bash
   python lottery_model.py
   ```

5. Výsledné grafy a metriky budú vykreslené na obrazovke, kde si môžeš pozrieť priebeh tréningu modelu.

## Výsledky

Výstupom tréningu je model, ktorý je schopný predikovať výherné čísla lotérie na základe historických dát. Výsledky sú prezentované vo forme grafov, ktoré zobrazujú presnosť modelu a priebeh učenia.

## Autor

Tento projekt bol vytvorený pre experimentálnu predikciu lotérie pomocou neurónových sietí. Slúži ako vzor pre prácu s dátami, normalizáciu a implementáciu základných modelov v PyTorch.
```
