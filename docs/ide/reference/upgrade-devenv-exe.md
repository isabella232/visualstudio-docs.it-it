---
title: -Upgrade (devenv.exe)
description: Informazioni su come usare l'opzione Aggiorna della riga di comando devenv per aggiornare il file della soluzione e tutti i relativi file di progetto o il file di progetto specificato nei formati di Visual Studio correnti per questi file.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2bb0565783efb27cf4194bb25982ee0f717be776
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040953"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)

Aggiorna il file della soluzione e tutti i relativi file di progetto oppure il file di progetto specificato ai formati di Visual Studio correnti per questi file.

## <a name="syntax"></a>Sintassi

```shell
devenv {SolutionFile|ProjectFile} /Upgrade [/Out OutputFilename]
```

## <a name="arguments"></a>Argomenti

- *SolutionFile*

  Obbligatorio se si aggiornano un'intera soluzione e i relativi progetti. Il percorso e il nome di un file di soluzione. È possibile immettere solo il nome del file di soluzione oppure il percorso completo e il nome del file di soluzione. Se la cartella o il file denominato non esiste ancora, viene creato.

- *ProjectFile*

  Obbligatorio se si esegue l'aggiornamento di un singolo progetto. Il percorso e il nome del file di progetto nella soluzione. È possibile immettere solo il nome del file di progetto oppure il percorso completo e il nome del file di progetto. Se la cartella o il file denominato non esiste ancora, viene creato.

- `/Out`*OutputFileName*

  facoltativo. Nome di un file a cui si vuole inviare l'output dello strumento. Se il file esiste già, lo strumento aggiunge l'output alla fine del file.

## <a name="remarks"></a>Osservazioni

I backup vengono creati e copiati automaticamente in una directory denominata Backup creata nella directory corrente.

Per consentire l'aggiornamento di soluzioni o progetti inclusi nel controllo del codice sorgente è necessario estrarli.

L'uso dell'opzione `/Upgrade` non apre Visual Studio. È possibile visualizzare i risultati dell'aggiornamento nel report di aggiornamento relativo al linguaggio di sviluppo della soluzione o del progetto. Non vengono restituiti messaggi di errore o informazioni sull'utilizzo. Per altre informazioni sull'aggiornamento di progetti in Visual Studio, vedere [Conversione, migrazione e aggiornamento dei progetti di Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md).

## <a name="example"></a>Esempio

Questo esempio aggiorna un file di soluzione denominato "MyProject.sln".

```shell
devenv "%USERPROFILE%\source\repos\MyProject\MyProject.sln" /upgrade
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
