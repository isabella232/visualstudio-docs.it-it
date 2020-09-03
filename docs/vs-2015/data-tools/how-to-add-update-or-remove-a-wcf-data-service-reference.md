---
title: 'Procedura: aggiungere, aggiornare o rimuovere un riferimento al servizio dati WCF | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 89a667e3254be8161d4defb54d524756a5eb02fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670014"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Procedura: aggiungere, aggiornare o rimuovere un riferimento al servizio dati WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un *riferimento al servizio* consente a un progetto di accedere a uno o più [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] . Utilizzare la finestra di dialogo **Aggiungi riferimento al servizio** per cercare [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] nella soluzione corrente, localmente, in una rete locale o su Internet.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="adding-a-service-reference"></a>Aggiunta di un riferimento al servizio

#### <a name="to-add-a-reference-to-an-external-service"></a>Per aggiungere un riferimento a un servizio esterno

1. In **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul nome del progetto a cui si desidera aggiungere il servizio, quindi fare clic su **Aggiungi riferimento al servizio**.

     Viene visualizzata la finestra di dialogo **Aggiungi riferimento al servizio**.

2. Nella casella **Indirizzo** immettere l'URL per il servizio, quindi fare clic su **Vai** per cercare il servizio. Se il servizio implementa la sicurezza del nome utente e della password, è possibile che venga richiesto di specificare un nome utente e una password.

    > [!NOTE]
    > Si consiglia di fare riferimento solo a servizi provenienti da un'origine attendibile. L'aggiunta di riferimenti da un'origine non attendibile può compromettere la sicurezza.

     È anche possibile selezionare l'URL nell'elenco **indirizzi** , che archivia i 15 URL precedenti in cui sono stati trovati i metadati del servizio validi.

     Quando viene eseguita la ricerca, viene visualizzato un indicatore di stato. È possibile arrestare la ricerca in qualsiasi momento facendo clic su **Interrompi**.

3. Nell'elenco **Servizi** espandere il nodo per il servizio che si desidera utilizzare e selezionare un set di entità.

4. Nella casella **Spazio dei nomi** immettere lo spazio dei nomi che si vuole usare per il riferimento.

5. Fare clic su **OK** per aggiungere il riferimento al progetto.

     Viene generato un client del servizio (proxy) e i metadati che descrivono il servizio vengono aggiunti al file di app.config.

#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Per aggiungere un riferimento a un servizio nella soluzione corrente

1. In **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul nome del progetto a cui si desidera aggiungere il servizio, quindi fare clic su **Aggiungi riferimento al servizio**.

     Viene visualizzata la finestra di dialogo **Aggiungi riferimento al servizio**.

2. Fare clic su **individua**.

     Tutti i servizi ( [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] e i servizi WCF) nella soluzione corrente vengono aggiunti all'elenco **dei servizi** .

3. Nell'elenco **Servizi** espandere il nodo per il servizio che si desidera utilizzare e selezionare un set di entità.

4. Nella casella **Spazio dei nomi** immettere lo spazio dei nomi che si vuole usare per il riferimento.

5. Fare clic su **OK** per aggiungere il riferimento al progetto.

     Viene generato un client del servizio (proxy) e i metadati che descrivono il servizio vengono aggiunti al file di app.config.

## <a name="updating-a-service-reference"></a>Aggiornamento di un riferimento al servizio
 I Entity Data Model per un oggetto [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] cambiano a volte. Quando si verifica questo problema, è necessario aggiornare il riferimento al servizio.

#### <a name="to-update-a-service-reference"></a>Per aggiornare un riferimento al servizio

- In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul riferimento al servizio, quindi scegliere **Aggiorna riferimento al servizio**.

     Viene visualizzata una finestra di dialogo di avanzamento mentre il riferimento viene aggiornato dal percorso originale e il client del servizio viene rigenerato per riflettere le modifiche apportate ai metadati.

## <a name="removing-a-service-reference"></a>Rimozione di un riferimento al servizio
 Se un riferimento al servizio non viene più usato, è possibile rimuoverlo dalla soluzione.

#### <a name="to-remove-a-service-reference"></a>Per rimuovere un riferimento al servizio

- In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul riferimento al servizio e scegliere **Elimina**.

     Il client del servizio verrà rimosso dalla soluzione e i metadati che descrivono il servizio verranno rimossi dal file di app.config.

    > [!NOTE]
    > Il codice che fa riferimento al riferimento al servizio dovrà essere rimosso manualmente.

## <a name="see-also"></a>Vedere anche
 [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
