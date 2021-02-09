---
title: "Procedura: creare un'associazione tra entità | Microsoft Docs"
description: Definire le relazioni tra entità nel modello di connettività dei dati aziendali (BDC) creando associazioni in Visual Studio.
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
ms.workload:
- office
ms.openlocfilehash: e726e8b5702a656b340401c9a2db26e40be1a37d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925566"
---
# <a name="how-to-create-an-association-between-entities"></a>Procedura: creare un'associazione tra entità
  È possibile definire le relazioni tra entità nel modello di integrazione applicativa dei dati (Business Data Connectivity) creando associazioni. Visual Studio genera metodi che forniscono agli utenti del modello informazioni sulle singole associazioni. Questi metodi possono essere utilizzati da elenchi, applicazioni personalizzate o web part di SharePoint per visualizzare le relazioni tra i dati in un'interfaccia utente.

 È possibile creare due tipi di associazioni nella finestra di progettazione dell'integrazione applicativa dei dati: associazioni basate su chiavi esterne e associazioni di chiavi esterne. Per altre informazioni, vedere [creare un'associazione tra le entità](../sharepoint/creating-an-association-between-entities.md).

### <a name="to-create-an-association-between-entities"></a>Per creare un'associazione tra entità

1. Nella scheda **BusinessDataConnectivity** della **casella degli strumenti** scegliere l'elemento **Association** .

2. Nella finestra di progettazione dell'integrazione applicativa dei dati scegliere l'entità di origine, quindi l'entità di destinazione.

     Verrà visualizzato l' **editor di associazione** .

3. Se si desidera creare un'associazione basata su chiave esterna, selezionare la casella di controllo **è associazione chiave esterna** .

    1. Nella colonna **ID origine** della tabella **mapping identificatore** scegliere l'identificatore accanto a ogni descrittore di tipo corrispondente visualizzato nella colonna **campo** .

         Ad esempio, nella colonna **ID origine** selezionare `ContactID` accanto al `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` descrittore di tipo e al `ReadItem.salesOrder.SalesOrder.ContactID` descrittore di tipo.

4. Se si desidera creare un'associazione di chiavi esterne, deselezionare la casella di controllo **è associazione chiave esterna** .

5. Fare clic su **OK** .

6. Nella finestra di progettazione dell'integrazione applicativa dei dati, viene visualizzata una riga che rappresenta l'associazione tra l'entità di origine e l'entità di destinazione.

     Visual Studio aggiunge un metodo dello strumento di navigazione dell'associazione alla classe di servizio dell'entità di destinazione e alla classe di servizio dell'entità di origine. Per ulteriori informazioni sui metodi di navigazione associati, vedere [operazioni supportate](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14)).

7. Nel metodo di associazione dello strumento di navigazione dell'entità di origine aggiungere il codice che restituisce una raccolta di entità di destinazione.

8. Nel metodo dello strumento di spostamento dell'associazione dell'entità di destinazione, aggiungere il codice che restituisce l'entità di origine correlata.

     Per esempi di metodi di associazione dello strumento di navigazione, vedere [creare un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md).

## <a name="see-also"></a>Vedi anche
- [Creare un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md)
- [Progettare un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Procedura: aggiungere un metodo di aggiornamento](../sharepoint/how-to-add-an-updater-method.md)
- [Panoramica degli strumenti di progettazione dei modelli BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Procedura: definire un'istanza di metodo](../sharepoint/how-to-define-a-method-instance.md)
- [Procedura: definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Procedura dettagliata: creare un elenco esterno in SharePoint usando i dati aziendali](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
