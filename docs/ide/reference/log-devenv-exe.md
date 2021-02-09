---
title: -Log (devenv.exe)
description: Informazioni su come usare l'opzione della riga di comando di devenv per registrare tutte le attività nel file di log per la risoluzione dei problemi.
ms.custom: SEO-VS-2020
ms.date: 12/12/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a7a4f8f3fc7fe0e0f8b7ff6bd460ea2efd8192d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919392"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Registra tutte le attività nel file di log per la risoluzione dei problemi. Il file verrà visualizzato dopo aver chiamato `devenv /log` almeno una volta. Per impostazione predefinita, il file di log è disponibile qui:

**% AppData% \\ActivityLog.xml\\ Microsoft \\ VisualStudio** \<Version\> **\\**

dove \<Version\> è la versione di Visual Studio. È tuttavia possibile specificare un percorso e un nome di file diversi.

## <a name="syntax"></a>Sintassi

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>Argomenti

- *NameOfLogFile*

  Obbligatorio. Percorso completo e nome del file di log in cui salvare le attività.

## <a name="remarks"></a>Commenti

Questa opzione deve apparire alla fine della riga di comando, dopo tutte le altre opzioni.

Il log viene scritto solo per tutte le istanze di Visual Studio aperte con l'opzione `/Log`.

## <a name="example"></a>Esempio

Questo esempio indirizza la registrazione al file `MyVSLog.xml` nella home directory dell'utente.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>Vedi anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
