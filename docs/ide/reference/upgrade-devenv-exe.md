---
title: -Upgrade (devenv.exe)
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
ms.openlocfilehash: 5bb2b296d8728587c9aa3c22b7a670d89612eff1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75596424"
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
