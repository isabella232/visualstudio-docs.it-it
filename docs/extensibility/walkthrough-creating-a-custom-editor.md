---
title: 'Procedura dettagliata: creazione di un editor personalizzato Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7eb376637fd72f3856415ee2527ec622fea02950
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697679"
---
# <a name="walkthrough-create-a-custom-editor"></a>Procedura dettagliata: Creare un editor personalizzatoWalkthrough: Create a custom editor
Il modello di progetto VSPackage è possibile creare un semplice editor personalizzato in C . Il modello di progetto VSPackage non supporta più i progetti in C o Visual Basic.The VSPackage project template no longer supports C'è or Visual Basic projects. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="prerequisites"></a>Prerequisiti
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="the-visual-studio-package-project-template"></a>Modello di progetto di pacchetto di Visual StudioThe Visual Studio Package project template
 È possibile trovare il modello di progetto di pacchetto di Visual Studio nella finestra di dialogo **Nuovo progetto** sotto la cartella **di estendibilità** di C.

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Per creare un pacchetto VSPackage usando il modello di pacchetto di Visual StudioTo create a VSPackage using the Visual Studio package template

1. Creare un progetto con il modello di pacchetto di Visual Studio.Create a project with the Visual Studio Package template.

2. Selezionare l'opzione **Editor personalizzato** e fare clic su **Avanti**. Viene visualizzata la pagina **Opzioni editor.**

3. Digitare il nome dell'editor nella casella **Nome editor.** Digitare l'estensione del file che si desidera associare all'editor nella casella **Estensione file.** L'editor è disponibile per i file con questa estensione. L'estensione del file viene registrata solo per Visual Studio, non per Windows. Digitare il nome file predefinito per i nuovi documenti creati con l'editor nella casella **Nome file predefinito.**

4. Fare clic su **Fine** per creare il pacchetto VSPackage nella cartella specificata.

### <a name="to-test-your-custom-editor"></a>Per testare l'editor personalizzato

1. Scegliere **Nuovo** dal menu **File** , quindi fare clic su **File**.

2. Nel riquadro **Modelli installati** della finestra di dialogo **Nuovo file** selezionare il modello di file, quindi il tipo di file registrato.

3. Fare clic su **Apri** per visualizzare e modificare il documento.

     L'editor supporta le operazioni di taglia e incolla, Trova e sostituisci e Apri e carica.

## <a name="see-also"></a>Vedere anche
- [Pacchetti VSPackage](../extensibility/internals/vspackages.md)
