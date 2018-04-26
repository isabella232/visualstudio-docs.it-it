---
title: Comando Apri soluzione
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 652305e6d5d360169645e7801e788b39b8982400
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="open-solution-command"></a>Comando Apri soluzione
Apre una soluzione esistente, chiudendo tutte le altre soluzioni aperte.

## <a name="syntax"></a>Sintassi

```
File.OpenSolution filename
```

## <a name="arguments"></a>Argomenti
 `Filename`

 Obbligatorio. Il percorso completo e nome file della soluzione da aprire.

 La sintassi per l'argomento `filename` richiede che i percorsi contenenti spazi usino le virgolette.

## <a name="remarks"></a>Note
 Il completamento automatico tenta di individuare il percorso e il nome file corretti durante la digitazione.

## <a name="example"></a>Esempio
 In questo esempio viene aperta la soluzione Test1.sln.

```
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)