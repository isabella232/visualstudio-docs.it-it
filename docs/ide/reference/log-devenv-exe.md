---
title: -Log (devenv.exe)
description: Informazioni su come usare l'opzione della riga di comando devenv log per registrare tutte le attività nel file di log per la risoluzione dei problemi.
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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 20972061208021ceea189c46e8e299a488748532e40eeed2544f28db13887efd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121357141"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Registra tutte le attività nel file di log per la risoluzione dei problemi. Il file verrà visualizzato dopo aver chiamato `devenv /log` almeno una volta. Per impostazione predefinita, il file di log è disponibile qui:

**%APPDATA% \\ Microsoft \\ VisualStudio \\** \<Version\> **\\ActivityLog.xml**

dove \<Version\> è la Visual Studio precedente. È tuttavia possibile specificare un percorso e un nome di file diversi.

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
