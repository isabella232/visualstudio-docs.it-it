---
title: Aggiungere, aggiornare o rimuovere un riferimento a WCF Data Services
description: Vedere come aggiungere, aggiornare o rimuovere un riferimento al servizio dati Windows Communication Foundation (WCF).
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 8d728df5f8af5dff5a7ea2456e1d40d47ddc7f76
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866892"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Procedura: Aggiungere, aggiornare o rimuovere un riferimento al servizio dati WCF

::: moniker range="vs-2017"
Un *riferimento al servizio* consente a un progetto di accedere a uno o più [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] . Utilizzare la finestra di dialogo **Aggiungi riferimento al servizio** per cercare [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] nella soluzione corrente, localmente, in una rete locale o su Internet.
::: moniker-end
::: moniker range=">=vs-2019"
È possibile usare il nodo **servizi connessi** in **Esplora soluzioni** per accedere al **Microsoft WCF Web Service Reference provider**, che consente di gestire i riferimenti al servizio dati Windows Communication Foundation (WCF).
::: moniker-end

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-wcf-service-reference"></a>Aggiungere un riferimento al servizio WCF

### <a name="to-add-a-reference-to-an-external-service"></a>Per aggiungere un riferimento a un servizio esterno

::: moniker range="vs-2017"

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nome del progetto a cui si desidera aggiungere il servizio, quindi fare clic su **Aggiungi riferimento al servizio**.

   Viene visualizzata la finestra di dialogo **Aggiungi riferimento al servizio**.

1. Nella casella **Indirizzo** immettere l'URL per il servizio, quindi fare clic su **Vai** per cercare il servizio. Se il servizio implementa la sicurezza del nome utente e della password, è possibile che venga richiesto di specificare un nome utente e una password.

    > [!NOTE]
    > Si consiglia di fare riferimento solo a servizi provenienti da un'origine attendibile. L'aggiunta di riferimenti da un'origine non attendibile può compromettere la sicurezza.

     È anche possibile selezionare l'URL nell'elenco **indirizzi** , che archivia i 15 URL precedenti in cui sono stati trovati i metadati del servizio validi.

     Quando viene eseguita la ricerca, viene visualizzato un indicatore di stato. È possibile arrestare la ricerca in qualsiasi momento facendo clic su **Interrompi**.

1. Nell'elenco **Servizi** espandere il nodo per il servizio che si desidera utilizzare e selezionare un set di entità.

1. Nella casella **Spazio dei nomi** immettere lo spazio dei nomi che si vuole usare per il riferimento.

1. Fare clic su **OK** per aggiungere il riferimento al progetto.

     Viene generato un client del servizio (proxy) e i metadati che descrivono il servizio vengono aggiunti al file di *app.config* .
::: moniker-end
::: moniker range=">=vs-2019"
1. In **Esplora soluzioni** fare doppio clic o toccare il nodo **servizi connessi** .

   Verrà visualizzata la scheda **Configura servizi** .

1. Scegliere **Microsoft WCF Web Service Reference provider**.

   Verrà visualizzata la finestra di dialogo **Configura riferimento al servizio Web WCF** .

   ![Screenshot della finestra di dialogo provider di servizi Web WCF](media/vs-2019/configure-wcf-web-service-reference-dialog.png)


1. Nella casella **URI** immettere l'URL per il servizio e quindi fare clic su **Vai** per cercare il servizio. Se il servizio implementa la sicurezza del nome utente e della password, è possibile che venga richiesto di specificare un nome utente e una password.

    > [!NOTE]
    > Si consiglia di fare riferimento solo a servizi provenienti da un'origine attendibile. L'aggiunta di riferimenti da un'origine non attendibile può compromettere la sicurezza.

     È anche possibile selezionare l'URL nell'elenco **URI** , in cui sono archiviati i 15 URL precedenti in cui sono stati trovati i metadati del servizio validi.

     Quando viene eseguita la ricerca, viene visualizzato un indicatore di stato. È possibile arrestare la ricerca in qualsiasi momento facendo clic su **Interrompi**.

1. Nell'elenco **Servizi** espandere il nodo per il servizio che si desidera utilizzare e selezionare un set di entità.

1. Nella casella **Spazio dei nomi** immettere lo spazio dei nomi che si vuole usare per il riferimento.

1. Fare clic su **fine** per aggiungere il riferimento al progetto.

     Viene generato un client del servizio (proxy) e i metadati che descrivono il servizio vengono aggiunti al file di *app.config* .

::: moniker-end

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Per aggiungere un riferimento a un servizio nella soluzione corrente

::: moniker range="vs-2017"

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nome del progetto a cui si desidera aggiungere il servizio, quindi fare clic su **Aggiungi riferimento al servizio**.

    Viene visualizzata la finestra di dialogo **Aggiungi riferimento al servizio**.

1. Fare clic su **individua**.

    Tutti i servizi ( [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] e i servizi WCF) nella soluzione corrente vengono aggiunti all'elenco **dei servizi** .

1. Nell'elenco **Servizi** espandere il nodo per il servizio che si desidera utilizzare e selezionare un set di entità.

1. Nella casella **Spazio dei nomi** immettere lo spazio dei nomi che si vuole usare per il riferimento.

1. Fare clic su **OK** per aggiungere il riferimento al progetto.

    Un client del servizio (proxy) genera e i metadati che descrivono il servizio vengono aggiunti al file di *app.config* .
::: moniker-end
::: moniker range=">=vs-2019"
1. In **Esplora soluzioni** fare doppio clic o toccare il nodo **servizi connessi** . 

   Verrà visualizzata la scheda **Configura servizi** .

1. Scegliere **Microsoft WCF Web Service Reference provider**.

   Verrà visualizzata la finestra di dialogo **Configura riferimento al servizio Web WCF** .

1. Fare clic su **individua**.

    Tutti i servizi ( [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] e i servizi WCF) nella soluzione corrente vengono aggiunti all'elenco **dei servizi** .

1. Nell'elenco **Servizi** espandere il nodo per il servizio che si desidera utilizzare e selezionare un set di entità.

1. Nella casella **Spazio dei nomi** immettere lo spazio dei nomi che si vuole usare per il riferimento.

1. Fare clic su **fine** per aggiungere il riferimento al progetto.

    Un client del servizio (proxy) genera e i metadati che descrivono il servizio vengono aggiunti al file di *app.config* .

::: moniker-end

## <a name="update-a-service-reference"></a>Aggiornare un riferimento al servizio

Il Entity Data Model per un oggetto [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] a volte cambia. Quando si verifica questo problema, è necessario aggiornare il riferimento al servizio.

### <a name="to-update-a-service-reference"></a>Per aggiornare un riferimento al servizio

- In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul riferimento al servizio, quindi scegliere **Aggiorna riferimento al servizio**.

     Viene visualizzata una finestra di dialogo dello stato di avanzamento quando il riferimento viene aggiornato dal percorso originale e il client del servizio viene rigenerato in modo da riflettere le modifiche apportate ai metadati.

## <a name="remove-a-service-reference"></a>Rimuovere un riferimento al servizio

Se un riferimento al servizio non viene più usato, è possibile rimuoverlo dalla soluzione.

### <a name="to-remove-a-service-reference"></a>Per rimuovere un riferimento al servizio

- In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul riferimento al servizio e scegliere **Elimina**.

     Il client del servizio verrà rimosso dalla soluzione e i metadati che descrivono il servizio verranno rimossi dal file di *app.config* .

    > [!NOTE]
    > Il codice che fa riferimento al riferimento al servizio deve essere rimosso manualmente.

## <a name="see-also"></a>Vedi anche

- [Servizi di Windows Communication Foundation e WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
