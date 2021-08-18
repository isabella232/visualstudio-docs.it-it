---
title: 'Procedura dettagliata: Creazione di un editor personalizzato | Microsoft Docs'
description: Informazioni su come il modello di progetto VSPackage può creare un semplice editor personalizzato in C++ usando questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8b2c06afa6391ea516d29e244ee869e21272bf0d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157930"
---
# <a name="walkthrough-create-a-custom-editor"></a>Procedura dettagliata: Creare un editor personalizzato
Il modello di progetto VSPackage può creare un semplice editor personalizzato in C++. Il modello di progetto VSPackage non supporta più progetti Visual Basic C#. Per altre informazioni, vedere [Visual Studio SDK.](../extensibility/visual-studio-sdk.md)

## <a name="prerequisites"></a>Prerequisiti
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="the-visual-studio-package-project-template"></a>Modello di Visual Studio pacchetto di distribuzione
 È possibile trovare il Visual Studio di progetto Package nella finestra di dialogo New Project (Nuovo **pacchetto)** nella **cartella Extensibility di C++.**

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Per creare un pacchetto VSPackage usando il modello Visual Studio pacchetto

1. Creare un progetto con il modello Visual Studio pacchetto.

2. Selezionare **l'opzione Editor** personalizzato e fare clic su **Avanti.** Verrà **visualizzata la pagina Opzioni** editor .

3. Digitare il nome dell'editor nella **casella Nome** editor . Digitare l'estensione di file che si vuole associare all'editor nella **casella Estensione** file . L'editor è disponibile per i file con questa estensione. L'estensione del file viene registrata solo per Visual Studio, non per Windows. Digitare il nome file predefinito per i nuovi documenti creati con l'editor nella **casella Nome file** predefinito .

4. Fare clic su **Fine** per creare il pacchetto VSPackage nella cartella specificata.

### <a name="to-test-your-custom-editor"></a>Per testare l'editor personalizzato

1. Scegliere **Nuovo** dal menu File **e** quindi fare clic su **File**.

2. Nel riquadro **Modelli installati** della finestra di dialogo **Nuovo file** selezionare il modello di file e quindi il tipo di file registrato.

3. Fare **clic su** Apri per visualizzare e modificare il documento.

     L'editor supporta le operazioni taglia e incolla, trova e sostituisci e le operazioni di apertura e caricamento.

## <a name="see-also"></a>Vedi anche
- [VSPackages](../extensibility/internals/vspackages.md)
