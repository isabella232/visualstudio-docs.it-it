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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ffe1d6cea14568f9d8859e005ee56bf45910348488864fe65f24c8b0512890de
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347201"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Procedura: Aggiungere, aggiornare o rimuovere un riferimento al servizio dati WCF

::: moniker range="vs-2017"
Un *riferimento al servizio* consente a un progetto di accedere a uno o più [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] . Usare la **Aggiungi riferimento al servizio** finestra di dialogo per cercare nella soluzione corrente, in locale, in una rete locale [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] o in Internet.
::: moniker-end
::: moniker range=">=vs-2019"
È possibile usare il **nodo Servizi connessi** in **Esplora soluzioni** per accedere al **Microsoft WCF Web Service Reference Provider**, che consente di gestire i riferimenti al servizio dati Windows Communication Foundation (WCF).
::: moniker-end

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-wcf-service-reference"></a>Aggiungere un riferimento al servizio WCF

### <a name="to-add-a-reference-to-an-external-service"></a>Per aggiungere un riferimento a un servizio esterno

::: moniker range="vs-2017"

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nome del progetto a cui si vuole aggiungere il servizio e quindi scegliere **Aggiungi riferimento al servizio**.

   Viene visualizzata la finestra di dialogo **Aggiungi riferimento al servizio**.

1. Nella casella **Indirizzo** immettere l'URL del servizio e quindi fare clic su **Vai** per cercare il servizio. Se il servizio implementa la sicurezza di nome utente e password, è possibile che venga richiesto di specificare un nome utente e una password.

    > [!NOTE]
    > Si consiglia di fare riferimento solo a servizi provenienti da un'origine attendibile. L'aggiunta di riferimenti da un'origine non attendibile può compromettere la sicurezza.

     È anche possibile selezionare l'URL **dall'elenco** Indirizzi, in cui sono archiviati i 15 URL precedenti in cui sono stati trovati metadati del servizio validi.

     Quando viene eseguita la ricerca, viene visualizzato un indicatore di stato. È possibile arrestare la ricerca in qualsiasi momento facendo clic su **Arresta**.

1. **Nell'elenco** Servizi espandere il nodo per il servizio che si vuole usare e selezionare un set di entità.

1. Nella casella **Spazio dei nomi** immettere lo spazio dei nomi che si vuole usare per il riferimento.

1. Fare clic su **OK** per aggiungere il riferimento al progetto.

     Viene generato un client del servizio (proxy) e i metadati che descrivono il servizio vengono aggiunti al file *app.config* servizio.
::: moniker-end
::: moniker range=">=vs-2019"
1. In **Esplora soluzioni** fare doppio clic o toccare il **Servizi connessi** nodo.

   Verrà **visualizzata la scheda Configura** servizi.

1. Scegliere **Microsoft WCF Web Service Reference Provider**.

   Verrà **visualizzata la WCF Web Service Reference** configurazione.

   ![Screenshot della finestra di dialogo Provider di servizi Web WCF](media/vs-2019/configure-wcf-web-service-reference-dialog.png)


1. Nella casella **URI** immettere l'URL del servizio e quindi fare clic su **Vai** per cercare il servizio. Se il servizio implementa la sicurezza di nome utente e password, è possibile che venga richiesto di specificare un nome utente e una password.

    > [!NOTE]
    > Si consiglia di fare riferimento solo a servizi provenienti da un'origine attendibile. L'aggiunta di riferimenti da un'origine non attendibile può compromettere la sicurezza.

     È anche possibile selezionare l'URL **dall'elenco URI,** in cui sono archiviati i 15 URL precedenti in cui sono stati trovati metadati del servizio validi.

     Quando viene eseguita la ricerca, viene visualizzato un indicatore di stato. È possibile arrestare la ricerca in qualsiasi momento facendo clic su **Arresta**.

1. **Nell'elenco** Servizi espandere il nodo per il servizio che si vuole usare e selezionare un set di entità.

1. Nella casella **Spazio dei nomi** immettere lo spazio dei nomi che si vuole usare per il riferimento.

1. Fare **clic su** Fine per aggiungere il riferimento al progetto.

     Viene generato un client del servizio (proxy) e i metadati che descrivono il servizio vengono aggiunti al file *app.config* servizio.

::: moniker-end

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Per aggiungere un riferimento a un servizio nella soluzione corrente

::: moniker range="vs-2017"

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nome del progetto a cui si vuole aggiungere il servizio e quindi scegliere **Aggiungi riferimento al servizio**.

    Viene visualizzata la finestra di dialogo **Aggiungi riferimento al servizio**.

1. Fare clic **su Individua**.

    Tutti i servizi [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] (entrambi e i servizi WCF) nella soluzione corrente vengono aggiunti all'elenco **Servizi.**

1. **Nell'elenco** Servizi espandere il nodo per il servizio che si vuole usare e selezionare un set di entità.

1. Nella casella **Spazio dei nomi** immettere lo spazio dei nomi che si vuole usare per il riferimento.

1. Fare clic su **OK** per aggiungere il riferimento al progetto.

    Viene generato un client del servizio (proxy) e i metadati che descrivono il servizio vengono aggiunti al file *app.config* servizio.
::: moniker-end
::: moniker range=">=vs-2019"
1. In **Esplora soluzioni** fare doppio clic o toccare il **Servizi connessi** nodo. 

   Verrà **visualizzata la scheda Configura** servizi.

1. Scegliere **Microsoft WCF Web Service Reference Provider**.

   Verrà **visualizzata la WCF Web Service Reference** configurazione.

1. Fare clic **su Individua**.

    Tutti i servizi [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] (entrambi e i servizi WCF) nella soluzione corrente vengono aggiunti all'elenco **Servizi.**

1. **Nell'elenco** Servizi espandere il nodo per il servizio che si vuole usare e selezionare un set di entità.

1. Nella casella **Spazio dei nomi** immettere lo spazio dei nomi che si vuole usare per il riferimento.

1. Fare **clic su** Fine per aggiungere il riferimento al progetto.

    Viene generato un client del servizio (proxy) e i metadati che descrivono il servizio vengono aggiunti al file *app.config* servizio.

::: moniker-end

## <a name="update-a-service-reference"></a>Aggiornare un riferimento al servizio

Il Entity Data Model per un oggetto [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] a volte cambia. In questo caso, è necessario aggiornare il riferimento al servizio.

### <a name="to-update-a-service-reference"></a>Per aggiornare un riferimento al servizio

- In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul riferimento al servizio e quindi scegliere **Aggiorna riferimento al servizio**.

     Viene visualizzata una finestra di dialogo di stato mentre il riferimento viene aggiornato dalla posizione originale e il client del servizio viene rigenerato per riflettere eventuali modifiche nei metadati.

## <a name="remove-a-service-reference"></a>Rimuovere un riferimento al servizio

Se un riferimento al servizio non viene più usato, è possibile rimuoverlo dalla soluzione.

### <a name="to-remove-a-service-reference"></a>Per rimuovere un riferimento al servizio

- In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul riferimento al servizio e quindi scegliere **Elimina**.

     Il client del servizio verrà rimosso dalla soluzione e i metadati che descrivono il servizio verranno rimossi dal file *app.config* file.

    > [!NOTE]
    > Qualsiasi codice che fa riferimento al riferimento al servizio deve essere rimosso manualmente.

## <a name="see-also"></a>Vedi anche

- [Windows Communication Foundation Services e servizi dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
