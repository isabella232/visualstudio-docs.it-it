---
description: La creazione di pacchetti di applicazioni come file MSI viene spesso eseguita usando l'estensione Programma di installazione di Visual Studio Projects.
title: Programma di installazione di Visual Studio Progetti e .NET Core 3.1 e .NET 5.0
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
ms.openlocfilehash: d1c756ce38a397b3dc7fe94a0d2627f1a55da9c2
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128426400"
---
# <a name="visual-studio-installer-projects-extension-and-net-core-31--net-50"></a>Programma di installazione di Visual Studio Estensione Projects e .NET Core 3.1/.NET 5.0

La creazione di pacchetti di applicazioni come file MSI viene spesso eseguita usando l'estensione Programma di installazione di Visual Studio Projects.

È possibile scaricare l'estensione qui: [Programma di installazione di Visual Studio Projects](https://marketplace.visualstudio.com/items?itemName=VisualStudioClient.MicrosoftVisualStudio2017InstallerProjects)

## <a name="update-for-net-core"></a>Aggiornamento per .NET Core
.NET Core ha due modelli diversi per la pubblicazione.

- Distribuzioni dipendenti dal framework

- Le applicazioni indipendenti includono il runtime.

Per altre informazioni su queste strategie di distribuzione, vedere Panoramica della pubblicazione di applicazioni [.NET Core.](/dotnet/core/deploying/)

### <a name="workflow-changes-for-net-core-31-and-net-50"></a>Modifiche del flusso di lavoro per .NET Core 3.1 e .NET 5.0

1. Selezionare **Pubblica elementi** anziché **Output** primario per ottenere l'output corretto per i progetti .NET Core 3.1 e .NET 5.0.  Per visualizzare questa finestra di dialogo, selezionare  >  **Project Output...** dal menu di scelta rapida del progetto.

    ![Gruppo di output Pubblica elementi nella finestra di dialogo Aggiungi gruppo di output Project pubblicazione](../deployment/media/installer-projects-net-core-publish-items-output.png "Selezionare Elementi di pubblicazione")

2. Per creare un programma di installazione autonomo, impostare  la **proprietà PublishProfilePath** nel nodo Elementi di pubblicazione nel progetto di installazione, usando il percorso relativo di un profilo di pubblicazione con le proprietà corrette impostate.

    ![Impostazione del profilo di pubblicazione nell'elemento di output del progetto Publish Items](../deployment/media/installer-projects-net-core-publish-profile.png "Impostare il profilo di pubblicazione")

>[!NOTE]
>Questo flusso di lavoro non è supportato per ASP.NET Core applicazioni, ma solo per Windows desktop.

### <a name="prerequisites-for-net-core-31-and-net-50"></a>Prerequisiti per .NET Core 3.1 e .NET 5.0

Se si vuole che il programma di installazione sia in grado di installare il runtime necessario per un'app .NET Core 3.1 o .NET 5.0 dipendente dal framework, è possibile eseguire questa operazione usando i [prerequisiti](../deployment/application-deployment-prerequisites.md).  Nella finestra di dialogo delle proprietà del progetto di installazione aprire la finestra di dialogo Prerequisiti **per** visualizzare le voci seguenti:

![Elementi .NET Core nella finestra di dialogo Prerequisiti](../deployment/media/installer-projects-net-core-prerequisites.png "Prerequisiti di .NET Core")

Per le applicazioni console è necessario selezionare l'opzione Runtime **.NET Core.** Per le applicazioni WPF/WinForms è necessario selezionare Runtime **.NET Desktop.**

>[!NOTE]
>Questi elementi sono presenti a partire dalla versione Visual Studio 2019 Update 7.

## <a name="see-also"></a>Vedi anche

- [Prerequisiti (finestra di dialogo)](../ide/reference/prerequisites-dialog-box.md)
- [Prerequisiti per la distribuzione di applicazioni](../deployment/application-deployment-prerequisites.md)
