---
title: 'Procedura dettagliata: creazione di un editor personalizzato | Microsoft Docs'
description: Per informazioni sul modello di progetto VSPackage, è possibile creare un semplice editor personalizzato in C++ usando questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0a4ebcf99634012943ed0a7fd1a72b5d4852729e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931383"
---
# <a name="walkthrough-create-a-custom-editor"></a>Procedura dettagliata: creare un editor personalizzato
Il modello di progetto VSPackage può creare un semplice editor personalizzato in C++. Il modello di progetto VSPackage non supporta più progetti C# o Visual Basic. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="prerequisites"></a>Prerequisiti
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="the-visual-studio-package-project-template"></a>Modello di progetto di pacchetto di Visual Studio
 È possibile trovare il modello di progetto di pacchetto di Visual Studio nella finestra di dialogo **nuovo progetto** nella cartella **Extensibility di C++** .

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Per creare un pacchetto VSPackage usando il modello di pacchetto di Visual Studio

1. Creare un progetto con il modello di pacchetto di Visual Studio.

2. Selezionare l'opzione **editor personalizzato** e fare clic su **Avanti**. Viene visualizzata la pagina **Opzioni editor** .

3. Digitare il nome dell'editor nella casella **nome editor** . Digitare l'estensione di file che si desidera associare all'editor nella casella **estensione file** . L'editor è disponibile per i file con questa estensione. L'estensione di file è registrata solo per Visual Studio, non per Windows. Digitare il nome file predefinito per i nuovi documenti creati con l'editor nella casella **nome file predefinito** .

4. Fare clic su **Fine** per creare il pacchetto VSPackage nella cartella specificata.

### <a name="to-test-your-custom-editor"></a>Per testare l'editor personalizzato

1. Scegliere **nuovo** dal menu **file** e quindi fare clic su **file**.

2. Nel riquadro **modelli installati** della finestra di dialogo **nuovo file** Selezionare il modello di file, quindi il tipo di file registrato.

3. Fare clic su **Apri** per visualizzare e modificare il documento.

     L'editor supporta le operazioni Taglia e incolla, la ricerca e la sostituzione e le operazioni di apertura e caricamento.

## <a name="see-also"></a>Vedi anche
- [VSPackages](../extensibility/internals/vspackages.md)
