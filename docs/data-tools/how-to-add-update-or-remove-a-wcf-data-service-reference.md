---
title: 'Procedura: aggiungere, aggiornare o rimuovere un riferimento al servizio dati WCF'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9099c1ee0b1ed3af108c11792f7629453dfbf7c6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819043"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Procedura: aggiungere, aggiornare o rimuovere un riferimento al servizio dati WCF
Oggetto *riferimento del servizio* consente a un progetto di accedere a uno o più [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]. Usare la **Aggiungi riferimento al servizio** finestra di dialogo per la ricerca [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] nella soluzione corrente, in locale, in una rete locale o su Internet.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-service-reference"></a>Aggiungere un riferimento al servizio

### <a name="to-add-a-reference-to-an-external-service"></a>Per aggiungere un riferimento a un servizio esterno

1.  Nelle **Esplora soluzioni**, fare doppio clic il nome del progetto a cui si desidera aggiungere il servizio e quindi fare clic su **Aggiungi riferimento al servizio**.

     Il **Aggiungi riferimento al servizio** verrà visualizzata la finestra di dialogo.

2.  Nel **indirizzi** casella, immettere l'URL per il servizio e quindi fare clic su **Vai** per cercare il servizio. Se il servizio implementa protezione nome e la password dell'utente, potrebbero essere richieste un nome utente e password.

    > [!NOTE]
    >  Si consiglia di fare riferimento solo a servizi provenienti da un'origine attendibile. L'aggiunta di riferimenti da un'origine non attendibile può compromettere la sicurezza.

     È anche possibile selezionare l'URL dal **indirizzo** elenco, che archivia gli URL precedenti 15 in corrispondenza del quale sono stati trovati i metadati di servizio valido.

     Consente di visualizzare un indicatore di stato quando viene eseguita la ricerca. È possibile arrestare la ricerca in qualsiasi momento facendo **arrestare**.

3.  Nel **Services** elenco, quindi espandere il nodo per il servizio che si desidera usare e selezionare un set di entità.

4.  Nel **Namespace** immettere lo spazio dei nomi che si desidera utilizzare per il riferimento.

5.  Fare clic su **OK** per aggiungere il riferimento al progetto.

     Viene generato un client del servizio (proxy) e i metadati che descrivono il servizio viene aggiunto per il *app. config* file.

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Per aggiungere un riferimento a un servizio nella soluzione corrente

1. Nelle **Esplora soluzioni**, fare doppio clic il nome del progetto a cui si desidera aggiungere il servizio e quindi fare clic su **Aggiungi riferimento al servizio**.

    Il **Aggiungi riferimento al servizio** verrà visualizzata la finestra di dialogo.

2. Fare clic su **individua**.

    Tutti i servizi (entrambi [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] e i servizi WCF) nella soluzione corrente vengono aggiunte per il **Services** elenco.

3. Nel **Services** elenco, quindi espandere il nodo per il servizio che si desidera usare e selezionare un set di entità.

4. Nel **Namespace** immettere lo spazio dei nomi che si desidera utilizzare per il riferimento.

5. Fare clic su **OK** per aggiungere il riferimento al progetto.

    Genera un client del servizio (proxy) e i metadati che descrivono il servizio viene aggiunto per il *app. config* file.

## <a name="update-a-service-reference"></a>Aggiornare un riferimento al servizio
 Entity Data Model per un [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] volte le modifiche apportate. In questo caso, è necessario aggiornare il riferimento al servizio.

### <a name="to-update-a-service-reference"></a>Per aggiornare un riferimento al servizio

-   Nelle **Esplora soluzioni**, fare riferimento al servizio e quindi fare clic su **Aggiorna riferimento al servizio**.

     Consente di visualizzare una finestra di dialogo di avanzamento viene aggiornato il riferimento dalla posizione originale, mentre il client del servizio viene rigenerato per riflettere le modifiche nei metadati.

## <a name="remove-a-service-reference"></a>Rimuovere un riferimento al servizio
 Se un riferimento al servizio non è più in uso, è possibile rimuoverlo dalla soluzione.

### <a name="to-remove-a-service-reference"></a>Per rimuovere un riferimento al servizio

-   Nelle **Esplora soluzioni**, fare riferimento al servizio e quindi fare clic su **eliminare**.

     Il client del servizio verrà rimosso dalla soluzione e i metadati che descrivono il servizio verranno rimosso dal *app. config* file.

    > [!NOTE]
    >  Qualsiasi codice che fa riferimento il servizio deve essere rimossi manualmente.

## <a name="see-also"></a>Vedere anche

- [Servizi dati di servizi Windows Communication Foundation e WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)