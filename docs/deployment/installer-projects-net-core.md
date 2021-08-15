---
description: La creazione di pacchetti di applicazioni come msi viene spesso eseguita usando l'Programma di installazione di Visual Studio projects.
title: Programma di installazione di Visual Studio Progetti e .NET Core 3.1
titleSuffix: ''
ms.date: 08/18/2020
ms.topic: conceptual
helpviewer_keywords:
- installer projects
- installer projects, .NETCore
author: MSLukeWest
ms.author: lukewest
manager: MSLukeWest
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 95e3b044c3f4f3ce72e15704874c2d8e03e3a2e3868ead006d1fab0635be9072
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121418447"
---
# <a name="visual-studio-installer-projects-extension-and-net-core-31"></a>Estensione Visual Studio Installer Projects e .NET Core 3.1

La creazione di pacchetti di applicazioni come msi viene spesso eseguita usando l'Programma di installazione di Visual Studio projects.

È possibile scaricare l'estensione qui: [Programma di installazione di Visual Studio Progetti](https://marketplace.visualstudio.com/items?itemName=VisualStudioClient.MicrosoftVisualStudio2017InstallerProjects)

## <a name="update-for-net-core"></a>Aggiornamento per .NET Core
.NET Core ha due modelli diversi per la pubblicazione.

- Distribuzioni dipendenti dal framework

- Le applicazioni indipendenti includono il runtime.

Per altre informazioni su queste strategie di distribuzione, vedere [Panoramica della pubblicazione di applicazioni .NET Core.](/dotnet/core/deploying/)

### <a name="workflow-changes-for-net-core-31"></a>Modifiche del flusso di lavoro per .NET Core 3.1

1. Selezionare **Pubblica elementi** anziché Output **primario** per ottenere l'output corretto per i progetti .NET Core 3.1.  Per visualizzare questa finestra di dialogo,  >  **selezionare Add Project Output...** (Aggiungi output del progetto) dal menu di scelta rapida del progetto.

    ![Gruppo di output Pubblica elementi nella finestra di dialogo Project gruppo di output](../deployment/media/installer-projects-net-core-publish-items-output.png "Selezionare Pubblica elementi")

2. Per creare un programma di installazione autonomo, impostare  la proprietà **PublishProfilePath** nel nodo Pubblica elementi nel progetto di installazione, usando il percorso relativo di un profilo di pubblicazione con le proprietà corrette impostate.

    ![Impostazione del profilo di pubblicazione nell'elemento di output del progetto Publish Items](../deployment/media/installer-projects-net-core-publish-profile.png "Impostare il profilo di pubblicazione")

### <a name="prerequisites-for-net-core-31"></a>Prerequisiti per .NET Core 3.1

Se si vuole che il programma di installazione sia in grado di installare il runtime necessario per un'app .NET Core 3.1 dipendente dal framework, è possibile eseguire questa operazione usando [i prerequisiti](../deployment/application-deployment-prerequisites.md).  Nella finestra di dialogo delle proprietà del progetto di installazione aprire la finestra di dialogo **Prerequisiti per** visualizzare le voci seguenti:

![Elementi di .NET Core nella finestra di dialogo Prerequisiti](../deployment/media/installer-projects-net-core-prerequisites.png "Prerequisiti di .NET Core")

**L'opzione Runtime di .NET Core deve** essere selezionata per le applicazioni console, Runtime desktop **.NET deve** essere selezionata per le applicazioni WPF/WinForms.

>[!NOTE]
>Questi elementi sono presenti a partire dalla versione Visual Studio 2019 Update 7.

## <a name="see-also"></a>Vedi anche

- [Prerequisiti (finestra di dialogo)](../ide/reference/prerequisites-dialog-box.md)
- [Prerequisiti per la distribuzione di applicazioni](../deployment/application-deployment-prerequisites.md)
