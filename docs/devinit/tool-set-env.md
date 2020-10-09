---
title: set-env
description: lo strumento devinit richiede-set-env.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 19f635f0d22eacd64726368af89bbf5b7c4c9a11
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862846"
---
# <a name="set-env"></a>set-env

Lo `set-env` strumento può essere utilizzato per impostare le variabili di ambiente da utilizzare nel processo corrente. Le variabili di ambiente vengono impostate solo nel processo corrente e verranno usate da altri `devinit` strumenti se vengono eseguite in tale processo.

Questo strumento usa l'API .NET Core `Environment.SetEnvironment` e presenta le stesse limitazioni dell'API. Per ulteriori informazioni, consultare la [documentazione](/dotnet/api/system.environment.setenvironmentvariable?preserve-view=true&view=netcore-3.1) relativa a `Environment.SetEnvironment` .

## <a name="usage"></a>Uso

| Nome                                         | Tipo   | Obbligatoria | valore                                                                       |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------|
| **Commenti**                                 | stringa | No       | Proprietà commenti facoltativi. Non usato.                                       |
| [**input**](#input)                          | stringa | No       | Input per lo strumento. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito.               |
| [**additionalOptions**](#additional-options) | stringa | No       | Non usato. Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.  |

### <a name="input"></a>Input

Lo `set-env` strumento accetta un'unica stringa come input per la `input` Proprietà. La stringa deve essere formattata con un punto e virgola (;) coppie chiave-valore delimitate (nome = valore) e quattro possibili azioni in base al valore della `input` Proprietà.

| Azione       | Input            | Descrizione                                                                                                                                                              | Esempio             |
|--------------|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| **list all** | Empty o omesso | Elencare tutte le variabili di ambiente correnti.                                                                                                                              | `"input":""`        |
| **elencarne uno** | string           | Elencare il valore di una variabile di ambiente specifica in base al nome.                                                                                                               | `"input":"foo"`     |
| **add**      | string           | Imposta il valore di una variabile di ambiente come coppia chiave-valore. Aggiunge una nuova variabile di ambiente se non è già presente o imposta il valore di una variabile di ambiente esistente | `"input":"foo=bar"` |
| **delete**   | string           | Elimina una variabile di ambiente esistente passando una stringa di valore vuota.                                                                                            | `"input":"foo="`    |

Una `input` stringa può contenere un'espansione della variabile di ambiente `%userprofile%` , ad esempio, che viene espansa quando viene letto il valore.

### <a name="additional-options"></a>Opzioni aggiuntive

Non usato.

## <a name="usage-in-a-codespace"></a>Utilizzo in un codespace

Se si usa un codespace, è possibile impostare le variabili di ambiente usate nello spazio dei Customizating tramite la `remoteEnv` proprietà nel [`.devcontainer.json`](/visualstudio/codespaces/reference/configuring) file.

## <a name="example-usage"></a>Esempio di utilizzo

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "comments": "A sample dot-devinit file demonstrating the set-env tool.",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=bar",
      "comments": "To set an environment variable, set input to 'name=value'."
    },
    {
      "tool": "set-env",
      "input": "foo",
      "comments": "To display the value of a single environment variable, set input to the name of the variable."
    },
    {
      "tool": "set-env",
      "comments": "To list all environment variables, pass no input."
    },
    {
      "tool": "set-env",
      "input": "foo=",
      "comments": "To delete an environment variable, pass input of 'name='."
    },
    {
      "tool": "set-env",
      "input": "foo",
      "comments": "Trying to display a variable that doesn't exist results in a warning."
    },
    {
      "tool": "set-env",
      "input": "_savedPath=%path%",
      "comments": "Envrionment variable expansion is supported."
    },
    {
      "tool": "set-env",
      "input": "path=%path%;%userprofile%\\CustomFolder",
      "comments": "Shows path manipulation. Note: Variables set here are not persisted."
    },
    {
      "tool": "set-env",
      "input": "path=%_savedPath%",
      "comments": "Restore path from saved copy."
    }
  ]
}
```