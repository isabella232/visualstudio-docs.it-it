---
title: "Procedura: Creare un'associazione tra entità | Microsoft Docs"
description: Definire le relazioni tra entità nel modello BDC (Business Data Connectivity) creando associazioni in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- AssociationGroupTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: b433262c93112c073145000b523d0aea6fb385b0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059998"
---
# <a name="how-to-create-an-association-between-entities"></a>Procedura: Creare un'associazione tra entità
  È possibile definire relazioni tra entità nel modello BDC (Business Data Connectivity) creando associazioni. Visual Studio genera metodi che forniscono ai consumer del modello informazioni su ogni associazione. Questi metodi possono essere utilizzati da elenchi, applicazioni personalizzate o web part di SharePoint per visualizzare le relazioni tra i dati in un'interfaccia utente.

 È possibile creare due tipi di associazioni in Progettazione BDC: associazioni basate su chiave esterna e associazioni senza chiave esterna. Per altre informazioni, vedere [Creare un'associazione tra entità.](../sharepoint/creating-an-association-between-entities.md)

### <a name="to-create-an-association-between-entities"></a>Per creare un'associazione tra entità

1. Nella scheda **BusinessDataConnectivity della** Casella degli **strumenti** scegliere l'elemento **Associazione.**

2. Nella finestra di progettazione dell'integrazione applicativa dei dati scegliere l'entità di origine, quindi l'entità di destinazione.

     Verrà **visualizzato l'Editor** associazione.

3. Se si desidera creare un'associazione basata su chiave esterna, selezionare la casella di **controllo Associazione chiave** esterna .

    1. Nella colonna **ID origine** della tabella **Mapping** identificatori scegliere l'identificatore accanto a ogni descrittore di tipo corrispondente visualizzato nella **colonna** Campo .

         Ad esempio, nella **colonna ID origine** selezionare accanto al descrittore di tipo e al `ContactID` `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` `ReadItem.salesOrder.SalesOrder.ContactID` descrittore di tipo.

4. Se si desidera creare un'associazione senza chiave esterna, deselezionare la casella di **controllo Associazione** chiave esterna .

5. Fare clic su **OK** .

6. In Progettazione integrazione applicativa dei dati viene visualizzata una linea che rappresenta l'associazione tra l'entità di origine e l'entità di destinazione.

     Visual Studio aggiunge un metodo Association Navigator alla classe del servizio dell'entità di destinazione e alla classe di servizio dell'entità di origine. Per altre informazioni sui metodi di navigazione di associazione, vedere [Operazioni supportate.](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14))

7. Nel metodo Association Navigator dell'entità di origine aggiungere il codice che restituisce una raccolta di entità di destinazione.

8. Nel metodo Association Navigator dell'entità di destinazione aggiungere il codice che restituisce l'entità di origine correlata.

     Per esempi di metodi association navigator, vedere [Creare un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md).

## <a name="see-also"></a>Vedi anche
- [Creare un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md)
- [Progettare un modello di connettività dei dati aziendali](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Procedura: Aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Procedura: Aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Procedura: Aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Procedura: Aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Procedura: Aggiungere un metodo updater](../sharepoint/how-to-add-an-updater-method.md)
- [Panoramica degli strumenti di progettazione del modello BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Procedura: Aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Procedura: Definire un'istanza del metodo](../sharepoint/how-to-define-a-method-instance.md)
- [Procedura: Definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Procedura dettagliata: Creare un elenco esterno in SharePoint usando i dati aziendali](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
