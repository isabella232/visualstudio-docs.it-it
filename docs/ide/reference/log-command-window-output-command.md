---
title: Comando Registra output finestra di comando
description: Informazioni sul comando Log Command Window Output (Output finestra di comando log) e su come copia tutto l'input e l'output dal finestra di comando in un file.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 30baf6cb3ed9a66d6c9d5696909f215e5721fcbd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151392"
---
# <a name="log-command-window-output-command"></a>Comando Registra output finestra di comando

Copia tutti gli input e gli output dalla **finestra di** comando in un file.

## <a name="syntax"></a>Sintassi

```cmd
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>Argomenti

`filename`\
facoltativo. Nome del file di log. Per impostazione predefinita, il file viene creato nella cartella del profilo dell'utente. Se il nome del file specificato esiste già, il log viene accodato alla fine del file esistente. Se non viene specificato alcun file, viene usato l'ultimo file specificato. Se non esiste alcun file precedente, viene creato un file di log predefinito, denominato cmdline.log.

> [!TIP]
> Per modificare il percorso in cui viene salvato il file di log, immettere il percorso completo del file, racchiuso tra virgolette se il percorso contiene spazi.

## <a name="switches"></a>Commutatori

/on\
facoltativo. Avvia la registrazione per la finestra di **comando** nel file specificato e accoda il file con le nuove informazioni.

/off\
facoltativo. Interrompe la registrazione per la finestra di **comando**.

/overwrite\
facoltativo. Se il file specificato nell'argomento `filename` corrisponde a un file esistente, il file viene sovrascritto.

## <a name="remarks"></a>Commenti

Se non viene specificato alcun file, viene creato per impostazione predefinita il file cmdline.log. Per impostazione predefinita, l'alias per questo comando è Log.

## <a name="examples"></a>Esempio

In questo esempio viene creato un nuovo file di log, cmdlog, e viene avviata la registrazione dei comandi.

```cmd
>Tools.LogCommandWindowOutput cmdlog
```

Questo esempio arresta la registrazione dei comandi.

```cmd
>Tools.LogCommandWindowOutput /off
```

Questo esempio consente di riprendere la registrazione dei comandi nel file di log usato in precedenza.

```cmd
>Tools.LogCommandWindowOutput /on
```

## <a name="see-also"></a>Vedi anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
