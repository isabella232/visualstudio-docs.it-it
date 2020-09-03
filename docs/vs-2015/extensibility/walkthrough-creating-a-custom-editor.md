---
title: 'Procedura dettagliata: creazione di un editor personalizzato | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b1b4e59e43a4a5aeb129464a34b96ef3f665e72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148862"
---
# <a name="walkthrough-creating-a-custom-editor"></a>Procedura dettagliata: creazione di un editor personalizzato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il modello di progetto VSPackage può creare un semplice editor personalizzato in C++.  Il modello di progetto VSPackage non supporta più progetti C# o Visual Basic. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="the-visual-studio-package-project-template"></a>Modello di progetto di pacchetto di Visual Studio  
 Il modello di progetto di pacchetto di Visual Studio è disponibile nella finestra di dialogo **nuovo progetto** nella cartella Extensibility C++  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Per creare un pacchetto VSPackage usando il modello di pacchetto di Visual Studio  
  
1. Creare un progetto con il modello di pacchetto di Visual Studio.  
  
2. Selezionare l'opzione **editor personalizzato** e fare clic su **Avanti**. Verrà visualizzata la pagina **Opzioni editor** .  
  
3. Digitare il nome dell'editor nella casella **nome editor** . Digitare l'estensione di file che si desidera associare all'editor nella casella **estensione file** . L'editor è disponibile per i file con questa estensione. L'estensione di file è registrata solo per Visual Studio, non per Windows. Digitare il nome file predefinito per i nuovi documenti creati con l'editor nella casella **nome file predefinito** .  
  
4. Fare clic su **Fine** per creare il pacchetto VSPackage nella cartella specificata.  
  
### <a name="to-test-your-custom-editor"></a>Per testare l'editor personalizzato  
  
1. Scegliere **nuovo** dal menu **file** e quindi fare clic su **file**.  
  
2. Nel riquadro **modelli installati** della finestra di dialogo **nuovo file** Selezionare il modello di file, quindi il tipo di file appena registrato.  
  
3. Fare clic su **Apri** per visualizzare e modificare il documento.  
  
     L'editor supporta le operazioni Taglia e incolla, la ricerca e la sostituzione e le operazioni di apertura e caricamento.  
  
## <a name="see-also"></a>Vedere anche  
 [VSPackages](../extensibility/internals/vspackages.md)
