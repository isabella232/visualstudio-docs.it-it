---
title: Configurare i pacchetti npm con package.json
description: Specificare le versioni dei pacchetti npm tramite package.json
ms.date: 09/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-javascript
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 9aaade6fc17b2ec0ce36decd66cff25ee2dc9e6e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061532"
---
# <a name="packagejson-configuration"></a>Configurazione di package.json

Se si sviluppa un'app Node.js con molti pacchetti npm, è probabile incorre in avvisi o errori durante la compilazione del progetto qualora uno o più pacchetti siano stati aggiornati. Può talvolta verificarsi un conflitto di versione o oppure può succedere che una versione del pacchetto sia stata deprecata. Di seguito sono riportati alcuni suggerimenti rapidi per configurare il file [package.json](https://docs.npmjs.com/files/package.json) e capire cosa accade quando vengono visualizzati avvisi o errori. Non si tratta di una guida completa al file *package.json*, ma solo di informazioni sul controllo delle versioni dei pacchetti npm.

Il sistema di controllo delle versioni dei pacchetti npm si attiene a regole molto precise. Il formato della versione è il seguente:

```
[major].[minor].[patch]
```

Supponiamo che l'app contenga un pacchetto con una versione 5.2.1. La versione principale è la 5, la versione secondaria è la 2 e la patch è la 1.

* In un aggiornamento della versione principale il pacchetto include nuove funzionalità che non sono compatibili con le versioni precedenti. Si tratta di modifiche che causano un'interruzione.
* In un aggiornamento della versione secondaria sono state aggiunte nuove funzionalità al pacchetto che sono compatibili con le versioni precedenti del pacchetto.
* In un aggiornamento della patch sono incluse una o più correzioni di bug. Le correzioni di bug sono sempre compatibili con le versioni precedenti.

Si noti che alcune funzionalità dei pacchetti npm presentano dipendenze. Ad esempio, per usare una nuova funzionalità del pacchetto di compilatori TypeScript (ts-loader) con webpack, potrebbe anche essere necessario eseguire l'aggiornamento del pacchetto npm di webpack e del pacchetto webpack-cli.

Per gestire il controllo delle versioni del pacchetto, npm supporta varie notazioni che è possibile usare nel file *package.json*. Le notazioni possono essere usate per controllare il tipo di aggiornamenti del pacchetto da accettare nell'app.

Si supponga di usare React e che sia necessario includere i pacchetti npm **react** e **react-dom**. È possibile specificarlo in modi diversi nel file *package.json*. Ad esempio, è possibile specificare l'uso della versione esatta di un pacchetto come indicato di seguito.

  ```json
  "dependencies": {
    "react": "16.4.2",
    "react-dom": "16.4.2",
  },
  ```

La notazione precedente indica a npm di usare sempre la versione esatta specificata, in questo caso la versione 16.4.2.

È possibile usare una notazione speciale per limitare gli aggiornamenti agli aggiornamenti della patch (correzioni di bug). Esempio:

  ```json
  "dependencies": {
    "react": "~16.4.2",
    "react-dom": "~16.4.2",
  },
  ```

Si usa il carattere tilde (~) per indicare a npm di usare soltanto un pacchetto se è stata applicata una patch. Npm può quindi eseguire l'aggiornamento di react 16.4.2 a 16.4.3 (o 16.4.4, e così via), ma non accetterà un aggiornamento alla versione principale o secondaria. La versione 16.4.2 non sarà pertanto aggiornata alla versione 16.5.0.

È anche possibile usare il simbolo di accento circonflesso (^) per specificare che npm può aggiornare il numero della versione secondaria.

  ```json
  "dependencies": {
    "react": "^16.4.2",
    "react-dom": "^16.4.2",
  },
  ```

Con questa notazione, npm può eseguire l'aggiornamento di react 16.4.2 a 16.5.0 (o 16.5.1, 16.6.0, e così via), ma non accetterà un aggiornamento alla versione principale. La versione 16.4.2 non sarà quindi aggiornata alla versione 17.0.0.

Dopo aver aggiornato i pacchetti, npm genera un file *package-lock.json* in cui sono elencate le effettive versioni di pacchetto usate nell'app, inclusi tutti i pacchetti annidati. Il file *package.json* controlla le dipendenze dirette per l'app, ma non controlla le dipendenze annidate. Sono necessari altri pacchetti npm per un pacchetto npm specifico. Durante il ciclo di sviluppo è possibile usare il file *package-lock.json* per assicurarsi che altri sviluppatori e tester stiano usando gli stessi pacchetti, inclusi i pacchetti annidati. Per altre informazioni, vedere [package-lock.json](https://docs.npmjs.com/files/package-lock.json) nella documentazione di npm.

Per Visual Studio, il file *package-lock.json* non viene aggiunto al progetto, ma è disponibile nella cartella di progetto.
