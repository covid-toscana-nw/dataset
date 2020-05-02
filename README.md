# Dati bollettini USL Toscana Nord Ovest

**Il presente è un repository non ufficiale, per uso strettamente sperimentale. Gli autori non assumono responsabilita' sulla correttezza e la completezza dei dati e lo stato di aggiornamento di essi.**

Dati ufficiali disponibili a https://www.uslnordovest.toscana.it/index.php/notizie. 

**Use at your own risk**

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Licenza Creative Commons" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />Quest'opera è distribuita con Licenza <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribuzione - Condividi allo stesso modo 4.0 Internazionale</a>.

## Contenuto del repository

### Dataset completo

Il dataset generato a partire dai file CSV è contenuto nel file `toscana_nw_all_datasets.json`. La struttura ad alto livello è la seguente:

```json
{
	"toscana" : { 
		"contagi-giornalieri":	{…},
		"contagi-totali":	{…},
		"decessi-giornalieri":	{…},
		"decessi-totali":	{…},
		"guariti-clinici-giornalieri":	{…},
		"guariti-clinici-totali":	{…},
		"positivi-attuali":	{…}
	},
	"aree" : [ ... ],
	"comuni": [ ... ],
	"provincie": [ ... ],
	"tasso-crescita" : [ ... ]
}
```

Per ciascun livello di aggregazione (totale, per aree, per comuni, per provincie) sono contenute diverse serie di dati, etichettate dalla loro denominazione.

Il formato di ogni serie è il formato richiesto da NgxCharts, ovvero:

```json
{
	"name": "NomeSerie",
	"series": [
		{ "name": "EtichettaAsseX", "value": 0 },
		...	
	]
}
```

### Registri dei dati

I record sono contenuti in file CSV nelle cartelle `contagi` e `decessi_e_guarigioni`.

All'interno delle cartelle, i file con suffisso `_all.csv` contengono la concatenazione degli altri file nella cartella, in ordine cronologico del dato contenuto. ***Importante: Non modificare manualmente, le modifiche vengono sovrascritte.***

Gli altri file contegono record per data e per comune (quando noto) di contagi, decessi, guarigioni virali e cliniche.

Per i ***contagi*** il formato dei dati è il seguente:

Posizione | Campo | Descrizione 
----------| ----- | ------------
1         | Data  | Giorno di pubblicazione del dato nel bollettino, formato YYYY-MM-DD
2         | Area  | Area di rilevazione del dato
3         | Comune  | Comune di rilevazione del date
4         | Numero nuovi contagi  | Numero intero dei nuovi contagi pubblicati nel giorno per il comune

Per ***decessi e guarigioni*** il formato dei dati è il seguente:

Posizione | Campo | Descrizione 
----------| ----- | ------------
1         | Data  | Giorno di pubblicazione del dato nel bollettino, formato YYYY-MM-DD
2         | Area  | Area di rilevazione del dato
3         | Comune  | Comune di rilevazione del date
4         | Numero nuovi decessi  | Numero intero dei nuovi decessi pubblicati nel giorno per il comune
5         | Numero nuovi guariti virali  | Numero intero dei nuovi guariti virali pubblicati nel giorno per il comune
6         | Numero nuovi guariti clinici  | Numero intero dei nuovi guariti clinici pubblicati nel giorno per il comune
