---
title: -Log (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93d3e4323638d40f003247a2c5bd35c812cc1c69
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
Registra tutte le attività nel file di log per la risoluzione dei problemi. Il file verrà visualizzato dopo aver chiamato `devenv /log` almeno una volta. Per impostazione predefinita, il file di log è:

 *%APPDATA%* \Microsoft\VisualStudio\\*Versione*\ActivityLog.xml

 dove *Versione* indica la versione di Visual Studio. È tuttavia possibile specificare un percorso e un nome di file diversi.

## <a name="syntax"></a>Sintassi

```
Devenv /log Path\NameOfLogFile
```

## <a name="remarks"></a>Note
 Questa opzione deve apparire alla fine della riga di comando, dopo tutte le altre opzioni.

 Il log viene scritto per tutte le istanze di Visual Studio richiamate con l'opzione /log. Non vengono registrate le istanze di Visual Studio richiamate senza l'opzione /log.

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)