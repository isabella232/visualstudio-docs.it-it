---
title: Creazione di un'associazione tra entità | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bf5c914ba998c7690a20d4e1a573f8344f976061
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870727"
---
# <a name="create-an-association-between-entities"></a>Creare un'associazione tra entità
  È possibile definire relazioni tra entità nel modello di integrazione applicativa dei dati (BDC) mediante la creazione di associazioni. Visual Studio genera i metodi che forniscono i consumer del modello con informazioni su ogni associazione. Questi metodi possono essere utilizzati da elenchi, applicazioni personalizzate o web part di SharePoint per visualizzare le relazioni tra i dati in un'interfaccia utente.  
  
## <a name="create-an-association"></a>Creare un'associazione
 Creare un'associazione, scegliere il **Association** controllo in Visual Studio **della casella degli strumenti**, scegliendo la prima entità (entità di origine denominata) e quindi scegliendo la seconda entità (denominato il entità di destinazione). È possibile definire i dettagli dell'associazione nel **Editor di associazione**. Per altre informazioni, vedere [Procedura: Creare un'associazione tra entità](../sharepoint/how-to-create-an-association-between-entities.md).  
  
## <a name="association-methods"></a>Metodi di associazione
 Le applicazioni, ad esempio web part di SharePoint aziendale dati usano le associazioni chiamando i metodi nella classe del servizio di un'entità. È possibile aggiungere metodi alla classe del servizio di un'entità, selezionandoli nel **Editor di associazione**.  
  
 Per impostazione predefinita, il **Editor di associazione** aggiunge un metodo di navigazione delle associazioni alle entità di origine e destinazione. Un metodo di associazione navigazione nell'entità di origine consente agli utenti di recuperare un elenco di entità di destinazione. Un metodo di associazione navigazione nell'entità di destinazione consente agli utenti di recuperare l'entità di origine che si riferisce a un'entità di destinazione.  
  
 È necessario aggiungere il codice per ognuno di questi metodi per restituire le informazioni appropriate. È anche possibile aggiungere altri tipi di metodi per supportare scenari più avanzati. Per altre informazioni su ciascuno di questi metodi, vedere [operazioni supportate](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
## <a name="types-of-associations"></a>Tipi di associazioni
 È possibile creare due tipi di associazioni nella finestra di progettazione integrazione applicativa dei dati: associazioni basate sulle chiavi esterne e associazioni senza chiave esterna.  
  
### <a name="foreign-key-based-association"></a>Associazione basato su chiavi esterne
 È possibile creare un'associazione basata su chiavi esterne in relazione con un identificatore dell'entità di origine al tipo descrittori definiti nell'entità di destinazione. Questa relazione consente agli utenti del modello fornire un'interfaccia utente avanzata per gli utenti. Ad esempio, un modulo in Outlook che consente all'utente di creare un ordine di vendita che possa visualizzare i clienti in un elenco a discesa; o un elenco di ordini di vendita in SharePoint che consente agli utenti di aprire una pagina del profilo per un cliente.  
  
 Per creare un'associazione basata su chiavi esterne, correlare gli identificatori e descrittori di tipo che condividono lo stesso nome e tipo. Ad esempio, è possibile creare un'associazione basata su chiavi esterne tra un `Contact` entità e un `SalesOrder` entità. Il `SalesOrder` entità restituisce una `ContactID` descrittore di tipo come parte del parametro restituito dal metodo Finder o Finder specifico. Entrambi i descrittori di tipo vengono visualizzati nei **Editor di associazione**. Per creare una relazione basata su chiave esterna tra le `Contact` entità e `SalesOrder` entità, scegliere il `ContactID` identificatore accanto a ognuno di questi campi.  
  
 Aggiungere codice al metodo AssociationNavigator dell'entità di origine che restituisce una raccolta di entità di destinazione. L'esempio seguente restituisce gli ordini di vendita per un contatto.  
  
 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]  
  
 Aggiungere codice al metodo AssociationNavigator dell'entità di destinazione che restituisce un'entità di origine. L'esempio seguente restituisce il contatto al quale è correlato all'ordine di vendita.  
  
 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]  
  
### <a name="foreign-keyless-association"></a>Associazione senza chiave esterna
 È possibile creare un'associazione senza mapping degli identificatori per i descrittori di tipo di campo. Creare questo tipo di associazione quando l'entità di origine non dispone di una relazione diretta con l'entità di destinazione. Ad esempio, un `SalesOrderDetail` tabella non dispone di una chiave esterna che esegue il mapping a una chiave primaria in un `Contact` tabella.  
  
 Se si desidera visualizzare le informazioni nel `SalesOrderDetail` tabella che si riferisce a un `Contact`, è possibile creare un'associazione senza chiave esterna tra le `Contact` entità e `SalesOrderDetail` entità.  
  
 Nel metodo AssociationNavigator della `Contact` entità, restituito il `SalesOrderDetail` entità unendo in join tabelle o chiamando una stored procedure.  
  
 L'esempio seguente restituisce i dettagli di tutti gli ordini di vendita unendo in join le tabelle.  
  
 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]  
  
 Nel metodo AssociationNavigator della `SalesOrderDetail` entità, restituisce i relativi `Contact`. Nell'esempio che segue viene illustrato quanto descritto.  
  
 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]  
  
## <a name="see-also"></a>Vedere anche
 [Progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Procedura: Creare un'associazione tra entità](../sharepoint/how-to-create-an-association-between-entities.md)  
