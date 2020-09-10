---
title: Progetti Programma di installazione di Visual Studio e .NET Core 3,1
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
ms.openlocfilehash: a057e655df643c5ddfd85064ba84260a2644dffd
ms.sourcegitcommit: 1803a67b516f67b209d8f4cf147314e604ef1927
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2020
ms.locfileid: "89641575"
---
# <a name="visual-studio-installer-projects-extension-and-net-core-31"></a>Estensione Visual Studio Installer Projects e .NET Core 3.1

La creazione di pacchetti di applicazioni come MSI viene spesso eseguita utilizzando l'estensione di progetti Programma di installazione di Visual Studio.

È possibile scaricare l'estensione qui: [programma di installazione di Visual Studio progetti](https://marketplace.visualstudio.com/items?itemName=VisualStudioClient.MicrosoftVisualStudio2017InstallerProjects)

## <a name="update-for-net-core"></a>Aggiornamento per .NET Core
.NET Core dispone di due modelli diversi per la pubblicazione.

- Distribuzioni dipendenti dal Framework

- Le applicazioni autosufficienti includono il runtime di.

Per ulteriori informazioni su queste strategie di distribuzione, vedere [Cenni preliminari sulla pubblicazione di applicazioni .NET Core](/dotnet/core/deploying/).

### <a name="workflow-changes-for-net-core-31"></a>Modifiche del flusso di lavoro per .NET Core 3,1

1. Selezionare **Pubblica elementi** anziché **output primario** per ottenere l'output corretto per i progetti .NET Core 3,1.  Per visualizzare questa finestra di dialogo, selezionare **Aggiungi**  >  **output progetto...** dal menu di scelta rapida del progetto.

    ![Gruppo output elementi di pubblicazione nella finestra di dialogo Aggiungi gruppo di output del progetto](../deployment/media/installer-projects-net-core-publish-items-output.png "Seleziona elementi di pubblicazione")

2. Per creare un programma di installazione autonomo, impostare la proprietà **PublishProfilePath** nel nodo **Publish Items** del progetto di installazione, usando il percorso relativo di un profilo di pubblicazione con le proprietà corrette impostate.

    ![Impostazione del profilo di pubblicazione nell'elemento di output del progetto elementi di pubblicazione](../deployment/media/installer-projects-net-core-publish-profile.png "Imposta profilo di pubblicazione")

### <a name="prerequisites-for-net-core-31"></a>Prerequisiti per .NET Core 3,1

Se si vuole che il programma di installazione sia in grado di installare il runtime necessario per un'app .NET Core 3,1 dipendente dal Framework, è possibile eseguire questa operazione usando i [prerequisiti](../deployment/application-deployment-prerequisites.md).  Nella finestra di dialogo delle proprietà del progetto di installazione, aprire la finestra di dialogo **prerequisiti...** e verranno visualizzate le voci seguenti:

![Elementi .NET Core nella finestra di dialogo Prerequisiti](../deployment/media/installer-projects-net-core-prerequisites.png "Prerequisiti di .NET Core")

Per le applicazioni console **è necessario selezionare** l'opzione **runtime di .NET Core.** .. per le applicazioni WPF/WinForms.

>[!NOTE]
>Questi elementi sono presenti a partire dalla versione di Visual Studio 2019 Update 7.

## <a name="see-also"></a>Vedi anche

- [Prerequisiti (finestra di dialogo)](../ide/reference/prerequisites-dialog-box.md)
- [Prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md)