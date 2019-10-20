---
title: -Log (devenv.exe)
ms.date: 12/12/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc37f4cd7441fc7945ca1762d16300c18d9ecbfe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610362"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Registra tutte le attività nel file di log per la risoluzione dei problemi. Il file verrà visualizzato dopo aver chiamato `devenv /log` almeno una volta. Per impostazione predefinita, il file di log è disponibile qui:

**%APPDATA%\\Microsoft\\VisualStudio\\** \<versione\> **\\ActivityLog.xml**

dove \<Versione\> indica la versione di Visual Studio. È tuttavia possibile specificare un percorso e un nome di file diversi.

## <a name="syntax"></a>Sintassi

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>argomenti

- *NameOfLogFile*

  Obbligatorio. Percorso completo e nome del file di log in cui salvare le attività.

## <a name="remarks"></a>Note

Questa opzione deve apparire alla fine della riga di comando, dopo tutte le altre opzioni.

Il log viene scritto solo per tutte le istanze di Visual Studio aperte con l'opzione `/Log`.

## <a name="example"></a>Esempio

Questo esempio indirizza la registrazione al file `MyVSLog.xml` nella home directory dell'utente.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)