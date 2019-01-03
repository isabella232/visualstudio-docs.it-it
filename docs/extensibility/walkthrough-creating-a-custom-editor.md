---
title: 'Procedura dettagliata: Creazione di un Editor personalizzato | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8656f14f3a6c9cd52b73ac0fdd3573d008c7aa0e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847154"
---
# <a name="walkthrough-create-a-custom-editor"></a>Procedura dettagliata: Creare un editor personalizzato
Il modello di progetto VSPackage può creare un semplice editor personalizzato in C++. Il modello di progetto VSPackage non supporta più progetti c# o Visual Basic. Per altre informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="the-visual-studio-package-project-template"></a>Il modello di progetto di pacchetto di Visual Studio  
 È possibile trovare il modello di progetto di pacchetto di Visual Studio nel **nuovo progetto** nella finestra di dialogo il **C++ estendibilità** cartella.  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Per creare un pacchetto VSPackage usando il modello di pacchetto di Visual Studio  
  
1.  Creare un progetto con il modello di pacchetto di Visual Studio.  
  
2.  Selezionare il **Editor personalizzato** opzione e fare clic su **successivo**. Il **le opzioni dell'Editor** verrà visualizzata la pagina.  
  
3.  Digitare il nome dell'editor nel **Editor nome** casella. Digitare l'estensione di file che si desidera essere associata con l'editor nel **estensione di File** casella. L'editor è disponibile per i file con questa estensione. L'estensione di file è registrata per Visual Studio solo, non per Windows. Digitare il nome file predefinito per i nuovi documenti creati con l'editor nel **nome File predefinito** casella.  
  
4.  Fare clic su **Fine** per creare il pacchetto VSPackage nella cartella specificata.  
  
### <a name="to-test-your-custom-editor"></a>Per eseguire il test dell'editor personalizzato  
  
1.  Nel **File** dal menu **New** e quindi fare clic su **File**.  
  
2.  Nel **modelli installati** riquadro della finestra di **nuovo File** finestra di dialogo, seleziona il modello di file, quindi il file di tipo è registrato.  
  
3.  Fare clic su **aperto** per visualizzare e modificare il documento.  
  
     L'editor supporta operazioni di taglia e Incolla, ricerca e sostituzione e open-and-load.  
  
## <a name="see-also"></a>Vedere anche  
 [Pacchetti VSPackage](../extensibility/internals/vspackages.md)