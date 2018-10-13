---
title: 'Procedura: aggiungere, aggiornare o rimuovere un riferimento al servizio dati WCF | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b14a83b195809dff89fa89bb6fcf91050e2f8a0c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192257"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Procedura: aggiungere, aggiornare o rimuovere un riferimento al servizio dati WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Oggetto *riferimento del servizio* consente a un progetto di accedere a uno o più [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]. Usare la **Aggiungi riferimento al servizio** finestra di dialogo per la ricerca [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] nella soluzione corrente, in locale, in una rete locale o su Internet.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="adding-a-service-reference"></a>Aggiunta di un riferimento al servizio  
  
#### <a name="to-add-a-reference-to-an-external-service"></a>Per aggiungere un riferimento a un servizio esterno  
  
1.  Nelle **Esplora soluzioni**, fare doppio clic il nome del progetto che si desidera aggiungere il servizio e quindi fare clic su **Aggiungi riferimento al servizio**.  
  
     Il **Aggiungi riferimento al servizio** verrà visualizzata la finestra di dialogo.  
  
2.  Nel **indirizzi** casella, immettere l'URL per il servizio e quindi fare clic su **Vai** per cercare il servizio. Se il servizio implementa protezione nome e la password dell'utente, potrebbero essere richieste un nome utente e password.  
  
    > [!NOTE]
    >  Si consiglia di fare riferimento solo a servizi provenienti da un'origine attendibile. L'aggiunta di riferimenti da un'origine non attendibile può compromettere la sicurezza.  
  
     È anche possibile selezionare l'URL dal **indirizzo** elenco, che archivia gli URL precedenti 15 in corrispondenza del quale sono stati trovati i metadati di servizio valido.  
  
     Un indicatore di stato viene visualizzato quando viene eseguita la ricerca. È possibile arrestare la ricerca in qualsiasi momento facendo **arrestare**.  
  
3.  Nel **Services** elenco, quindi espandere il nodo per il servizio che si desidera usare e selezionare un set di entità.  
  
4.  Nel **Namespace** immettere lo spazio dei nomi che si desidera utilizzare per il riferimento.  
  
5.  Fare clic su **OK** per aggiungere il riferimento al progetto.  
  
     Viene generato un client del servizio (proxy) e i metadati che descrivono il servizio viene aggiunto al file app. config.  
  
#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Per aggiungere un riferimento a un servizio nella soluzione corrente  
  
1.  Nelle **Esplora soluzioni**, fare doppio clic il nome del progetto che si desidera aggiungere il servizio e quindi fare clic su **Aggiungi riferimento al servizio**.  
  
     Il **Aggiungi riferimento al servizio** verrà visualizzata la finestra di dialogo.  
  
2.  Fare clic su **individua**.  
  
     Tutti i servizi (entrambi [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] e i servizi WCF) nella soluzione corrente vengono aggiunte per il **Services** elenco.  
  
3.  Nel **Services** elenco, quindi espandere il nodo per il servizio che si desidera usare e selezionare un set di entità.  
  
4.  Nel **Namespace** immettere lo spazio dei nomi che si desidera utilizzare per il riferimento.  
  
5.  Fare clic su **OK** per aggiungere il riferimento al progetto.  
  
     Viene generato un client del servizio (proxy) e i metadati che descrivono il servizio viene aggiunto al file app. config.  
  
## <a name="updating-a-service-reference"></a>L'aggiornamento di un riferimento al servizio  
 Entity Data Model per un [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] viene talvolta modificato. Quando in questo caso, è necessario aggiornare il riferimento al servizio.  
  
#### <a name="to-update-a-service-reference"></a>Per aggiornare un riferimento al servizio  
  
-   Nelle **Esplora soluzioni**, fare riferimento al servizio e quindi fare clic su **Aggiorna riferimento al servizio**.  
  
     Il riferimento viene aggiornato dalla posizione originale, mentre il client del servizio viene rigenerato per riflettere le modifiche nei metadati, viene visualizzata una finestra di dialogo lo stato di avanzamento.  
  
## <a name="removing-a-service-reference"></a>Rimozione di un riferimento al servizio  
 Se un riferimento al servizio non è più in uso, è possibile rimuoverlo dalla soluzione.  
  
#### <a name="to-remove-a-service-reference"></a>Per rimuovere un riferimento al servizio  
  
-   Nelle **Esplora soluzioni**, fare riferimento al servizio e quindi fare clic su **eliminare**.  
  
     Il client del servizio verrà rimosso dalla soluzione e i metadati che descrivono il servizio verranno rimosso dal file app. config.  
  
    > [!NOTE]
    >  Qualsiasi codice che fa riferimento il servizio deve essere rimosso manualmente.  
  
## <a name="see-also"></a>Vedere anche  
 [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

