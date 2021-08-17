---
title: Creazione di un'associazione tra entità | Microsoft Docs
description: Creare un'associazione tra entità nel modello BDC (Business Data Connectivity). Informazioni sui metodi di associazione e sui tipi di associazioni.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Association_Dialog
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
ms.openlocfilehash: 46536fc9a0767cbd5ff6d1a682e5e8545b1329ff94139530af0e7167d0ecad6a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121228935"
---
# <a name="create-an-association-between-entities"></a>Creare un'associazione tra entità
  È possibile definire relazioni tra entità nel modello BDC (Business Data Connectivity) creando associazioni. Visual Studio genera metodi che forniscono ai consumer del modello informazioni su ogni associazione. Questi metodi possono essere utilizzati da elenchi, applicazioni personalizzate o web part di SharePoint per visualizzare le relazioni tra i dati in un'interfaccia utente.

## <a name="create-an-association"></a>Creare un'associazione
 Creare un'associazione  scegliendo il controllo Associazione nella casella degli strumenti Visual Studio **,** scegliendo la prima entità (denominata entità di origine) e quindi scegliendo la seconda entità (denominata entità di destinazione). È possibile definire i dettagli dell'associazione in **Editor associazioni**. Per altre informazioni, vedere [Procedura: Creare un'associazione tra entità](../sharepoint/how-to-create-an-association-between-entities.md).

## <a name="association-methods"></a>Metodi di associazione
 Le applicazioni come SharePoint web part di dati aziendali utilizzano le associazioni chiamando metodi nella classe di servizio di un'entità. È possibile aggiungere metodi alla classe di servizio di un'entità selezionandoli **nell'Editor associazioni**.

 Per impostazione predefinita, **l'editor di associazione** aggiunge un metodo di navigazione associazione alle entità di origine e di destinazione. Un metodo di navigazione associazione nell'entità di origine consente ai consumer di recuperare un elenco di entità di destinazione. Un metodo di navigazione associazione nell'entità di destinazione consente ai consumer di recuperare l'entità di origine correlata a un'entità di destinazione.

 È necessario aggiungere il codice a ognuno di questi metodi per restituire le informazioni appropriate. È anche possibile aggiungere altri tipi di metodi per supportare scenari più avanzati. Per altre informazioni su ognuno di questi metodi, vedere [Operazioni supportate](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14)).

## <a name="types-of-associations"></a>Tipi di associazioni
 È possibile creare due tipi di associazioni nella finestra di progettazione del data center BDC: associazioni basate su chiave esterna e associazioni senza chiave esterna.

### <a name="foreign-key-based-association"></a>Associazione basata su chiave esterna
 È possibile creare un'associazione basata su chiave esterna, relazionando un identificatore nell'entità di origine ai descrittori di tipo definiti nell'entità di destinazione. Questa relazione consente ai consumer del modello di fornire un'interfaccia utente avanzata per gli utenti. Ad esempio, un modulo in Outlook che consente a un utente di creare un ordine di vendita in grado di visualizzare i clienti in un elenco a discesa; o un elenco di ordini di vendita in SharePoint che consente agli utenti di aprire una pagina del profilo per un cliente.

 Per creare un'associazione basata su chiave esterna, correlare gli identificatori e i descrittori di tipo che condividono lo stesso nome e tipo. Ad esempio, è possibile creare un'associazione basata su chiave esterna tra `Contact` un'entità e `SalesOrder` un'entità. `SalesOrder`L'entità restituisce un `ContactID` descrittore di tipo come parte del parametro restituito dei metodi Finder o Finder specifici. Entrambi i descrittori di tipo vengono visualizzati **nell'Editor associazioni**. Per creare una relazione basata su chiave esterna tra l'entità e l'entità, `Contact` scegliere l'identificatore accanto a ognuno di questi `SalesOrder` `ContactID` campi.

 Aggiungere il codice al metodo Association Navigator dell'entità di origine che restituisce una raccolta di entità di destinazione. Nell'esempio seguente vengono restituiti gli ordini di vendita per un contatto.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet7":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet7":::

 Aggiungere il codice al metodo Association Navigator dell'entità di destinazione che restituisce un'entità di origine. Nell'esempio seguente viene restituito il contatto correlato all'ordine di vendita.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs" id="Snippet8":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb" id="Snippet8":::

### <a name="foreign-keyless-association"></a>Associazione senza chiave esterna
 È possibile creare un'associazione senza eseguire il mapping degli identificatori ai descrittori dei tipi di campo. Creare questo tipo di associazione quando l'entità di origine non ha una relazione diretta con l'entità di destinazione. Ad esempio, una tabella non dispone di una chiave esterna che esegue il `SalesOrderDetail` mapping a una chiave primaria in una `Contact` tabella.

 Se si desidera visualizzare informazioni nella tabella correlate a , è possibile creare un'associazione senza chiave esterna `SalesOrderDetail` tra l'entità `Contact` e `Contact` `SalesOrderDetail` l'entità.

 Nel metodo di navigazione associazione dell'entità, restituire le entità unendo le tabelle o chiamando `Contact` `SalesOrderDetail` un stored procedure.

 Nell'esempio seguente vengono restituiti i dettagli di tutti gli ordini di vendita tramite join di tabelle.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet9":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet9":::

 Nel metodo di navigazione associazione `SalesOrderDetail` dell'entità, restituire l'oggetto `Contact` correlato. L'esempio seguente illustra questa operazione.
                                                                            
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs" id="Snippet10":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb" id="Snippet10":::

## <a name="see-also"></a>Vedi anche
- [Progettare un modello di connettività dei dati aziendali](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Procedura: Creare un'associazione tra entità](../sharepoint/how-to-create-an-association-between-entities.md)
