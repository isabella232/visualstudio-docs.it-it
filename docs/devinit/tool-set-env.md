---
title: set-env
description: lo strumento devinit richiede-set-env.
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
ms.openlocfilehash: 82f0def521a7a5a6bf4bd4595d32775324a0a39c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171022"
---
# <a name="set-env"></a>set-env

Lo `set-env` strumento può essere utilizzato per impostare le variabili di ambiente da utilizzare nel processo corrente. Le variabili di ambiente vengono impostate solo nel processo corrente e verranno usate da altri `devinit` strumenti se vengono eseguite in tale processo.

Questo strumento usa l'API .NET Core `Environment.SetEnvironment` e presenta le stesse limitazioni dell'API. Per ulteriori informazioni, consultare la [documentazione](/dotnet/api/system.environment.setenvironmentvariable?view=netcore-3.1&preserve-view=true) relativa a `Environment.SetEnvironment` .

## <a name="usage"></a>Utilizzo

| Nome                                         | Tipo   | Obbligatoria | valore                                                                       |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------|
| **Commenti**                                 | stringa | No       | Proprietà commenti facoltativi. Non usato.                                       |
| [**input**](#input)                          | stringa | No       | Input per lo strumento. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito.               |
| [**additionalOptions**](#additional-options) | stringa | No       | Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.            |

### <a name="input"></a>Input

Lo `set-env` strumento accetta un'unica stringa come input per la `input` Proprietà. La stringa deve essere formattata con un punto e virgola (;) coppie chiave-valore delimitate (nome = valore) e quattro possibili azioni in base al valore della `input` Proprietà.

| Azione       | Input            | Descrizione                                                                                                                                                              | Esempio             |
|--------------|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| **list all** | Empty o omesso | Elencare tutte le variabili di ambiente correnti.                                                                                                                           | `"input":""`        |
| **elencarne uno** | string           | Elencare il valore di una variabile di ambiente specifica in base al nome.                                                                                                               | `"input":"foo"`     |
| **add**      | string           | Imposta il valore di una variabile di ambiente come coppia chiave-valore. Aggiunge una nuova variabile di ambiente se non è già presente o imposta il valore di una variabile di ambiente esistente | `"input":"foo=bar"` |
| **delete**   | string           | Elimina una variabile di ambiente esistente passando una stringa di valore vuota.                                                                                            | `"input":"foo="`    |

Una `input` stringa può contenere un'espansione della variabile di ambiente `%userprofile%` , ad esempio, che viene espansa quando viene letto il valore.

### <a name="additional-options"></a>Opzioni aggiuntive

 `--user``--process` `--machine` è possibile includere, o per specificare dove impostare le variabili di ambiente. Per impostazione predefinita, la destinazione è l'utente. Per ulteriori informazioni sulle destinazioni possibili per le variabili di ambiente, vedere [EnvironmentVariableTarget](https://docs.microsoft.com/dotnet/api/system.environmentvariabletarget).

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `set-env` strumento consiste nell'elencare tutte le variabili di ambiente correnti.

## <a name="usage-in-a-codespace"></a>Utilizzo in un codespace

Se si usa un codespace, è possibile impostare le variabili di ambiente usate nello spazio dei caratteri tramite la personalizzazione della `remoteEnv` proprietà nel [`.devcontainer.json`](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) file.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito sono riportati alcuni esempi di come eseguire `set-env` usando un `.devinit.json` .

#### <a name="devinitjson-that-will-set-an-environment-variable-foo-to-value-bar"></a>.devinit.json che imposta una variabile di ambiente, `foo` , su value `bar` :
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

#### <a name="devinitjson-that-will-set-an-environment-variable-foo-to-value-bar-stored-in-the-environment-block-associated-with-the-current-process"></a>.devinit.json che imposta una variabile di ambiente, `foo` , su value, `bar` , archiviata nel blocco dell'ambiente associato al processo corrente:
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

#### <a name="devinitjson-that-will-display-the-value-of-an-environment-variable"></a>.devinit.jssu in cui viene visualizzato il valore di una variabile di ambiente:
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

#### <a name="devinitjson-that-will-list-all-the-environment-variables"></a>.devinit.jssu in cui sono elencate tutte le variabili di ambiente:
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


#### <a name="devinitjson-that-will-use-environment-variable-expansion"></a>.devinit.jsin che utilizzerà l'espansione delle variabili di ambiente:
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

#### <a name="devinitjson-that-will-set-an-environment-variable-value-using-path-manipulation"></a>.devinit.json che imposta un valore della variabile di ambiente mediante la manipolazione del percorso:
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

#### <a name="devinitjson-that-will-restore-path-from-saved-copy"></a>.devinit.json che ripristinerà il percorso dalla copia salvata:
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
