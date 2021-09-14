---
title: set-env
description: devinit tool require-set-env.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 86e6f7c22ac75d976050858eb2853f9036377fee
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709843"
---
# <a name="set-env"></a>set-env

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione a GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è rivolta alle esperienze in continua evoluzione per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro Visual Studio cloud. Nell'ambito di `devinit` questo e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo `set-env` strumento può essere usato per impostare le variabili di ambiente da usare nel processo corrente. Le variabili di ambiente vengono impostate solo nel processo corrente e verranno usate da altri `devinit` strumenti se vengono eseguite in tale processo.

Questo strumento usa l'API .NET Core `Environment.SetEnvironment` e presenta le stesse limitazioni di tale API. Per altre informazioni, vedere la [documentazione](/dotnet/api/system.environment.setenvironmentvariable?view=netcore-3.1&preserve-view=true) per `Environment.SetEnvironment` .

## <a name="usage"></a>Utilizzo

| Nome                                         | Tipo   | Obbligatoria | valore                                                                       |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------|
| **Commenti**                                 | stringa | No       | Proprietà comments facoltativa. Non usato.                                       |
| [**Input**](#input)                          | stringa | No       | Input per lo strumento. Per informazioni [dettagliate,](#input) vedere Input di seguito.               |
| [**additionalOptions**](#additional-options) | stringa | No       | Per [informazioni dettagliate, vedere](#additional-options) Opzioni aggiuntive di seguito.            |

### <a name="input"></a>Input

Lo `set-env` strumento accetta una singola stringa come input per la proprietà `input` . La stringa deve essere formattata come stringa di punto e virgola (;) coppie chiave-valore delimitate (name=value) e quattro azioni possibili in base al valore della `input` proprietà .

| Azione       | Input            | Descrizione                                                                                                                                                              | Esempio             |
|--------------|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| **list all** | vuoto o omesso | Elenca tutte le variabili di ambiente correnti.                                                                                                                           | `"input":""`        |
| **list one** | string           | Elencare il valore di una variabile di ambiente specifica in base al nome.                                                                                                               | `"input":"foo"`     |
| **add**      | string           | Imposta il valore di una variabile di ambiente come coppia chiave-valore. Aggiunge una nuova variabile di ambiente se non è già presente o imposta il valore di una variabile di ambiente esistente | `"input":"foo=bar"` |
| **delete**   | string           | Elimina una variabile di ambiente esistente passando una stringa di valore vuota.                                                                                            | `"input":"foo="`    |

Una `input` stringa può contenere un'espansione della variabile di ambiente, ad esempio , che viene `%userprofile%` espansa quando viene letto il valore.

### <a name="additional-options"></a>Opzioni aggiuntive

 `--user`È `--process` possibile includere , o per specificare dove impostare le variabili di `--machine` ambiente. Per impostazione predefinita, la destinazione è l'utente. Per altre informazioni sulle possibili destinazioni per le variabili di ambiente, vedere [EnvironmentVariableTarget.](https://docs.microsoft.com/dotnet/api/system.environmentvariabletarget)

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello strumento `set-env` è elencare tutte le variabili di ambiente correnti.

## <a name="usage-in-a-codespace"></a>Utilizzo in un codespace

Se si usa uno spazio di codice, è possibile impostare le variabili di ambiente usate nello spazio di codice personalizzando `remoteEnv` la proprietà nel file [`.devcontainer.json`](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) .

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito sono riportati esempi di come eseguire `set-env` usando `.devinit.json` un oggetto .

#### <a name="devinitjson-that-will-set-an-environment-variable-foo-to-value-bar"></a>.devinit.json che imposta una variabile di ambiente, `foo` , sul valore `bar` :
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=bar",
    }
  ]
}
```

#### <a name="devinitjson-that-will-set-an-environment-variable-foo-to-value-bar-stored-in-the-environment-block-associated-with-the-current-process"></a>.devinit.json che imposta una variabile di ambiente, , sul valore , archiviata nel blocco di `foo` ambiente associato al processo `bar` corrente:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=bar",
      "additionalOptions": "--process",
    }
  ]
}
```

#### <a name="devinitjson-that-will-display-the-value-of-an-environment-variable"></a>.devinit.json che visualizza il valore di una variabile di ambiente:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo",
    }
  ]
}
```

#### <a name="devinitjson-that-will-list-all-the-environment-variables"></a>.devinit.json che elenca tutte le variabili di ambiente:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
    }
  ]
}
```

#### <a name="devinitjson-that-will-delete-an-environment-variable"></a>.devinit.json che eliminerà una variabile di ambiente:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=",
    }
  ]
}
```


#### <a name="devinitjson-that-will-use-environment-variable-expansion"></a>.devinit.json che userà l'espansione della variabile di ambiente:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "_savedPath=%path%",
    }
  ]
}
```

#### <a name="devinitjson-that-will-set-an-environment-variable-value-using-path-manipulation"></a>.devinit.json che imposta il valore di una variabile di ambiente usando la modifica del percorso:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "path=%path%;%userprofile%\\CustomFolder",
    }
  ]
}
```

#### <a name="devinitjson-that-will-restore-path-from-saved-copy"></a>.devinit.json che ripristina il percorso dalla copia salvata:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "path=%_savedPath%",
    }
  ]
}
```
