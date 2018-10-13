---
title: Configurare Service Reference Dialog Box | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 24da338378739afca6ad228582a29069aebde9f5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266981"
---
# <a name="configure-service-reference-dialog-box"></a>Configura riferimento a servizio (finestra di dialogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Il **Configura riferimento al servizio** finestra di dialogo consente di configurare il comportamento di [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] servizi.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere Importa/esporta impostazioni dal menu Strumenti. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Per l'accesso di **Configura riferimento al servizio** della finestra di dialogo scelta di un servizio fa riferimento nel **Esplora soluzioni** e scegliere **Configura riferimento al servizio**. È anche possibile accedere nella finestra di dialogo facendo clic la **avanzate** pulsante il **Add Service Reference Dialog Box**.  
  
## <a name="task-list"></a>Elenco attività  
  
-   Per modificare l'indirizzo in cui è ospitato un servizio WCF, immettere il nuovo indirizzo nella **indirizzo** campo.  
  
-   Per modificare il livello di accesso per le classi in un client WCF, selezionare una parola chiave a livello di accesso nel **livello di accesso per classi generate** elenco.  
  
-   Per chiamare i metodi di un servizio WCF in modo asincrono, selezionare la **Genera operazioni asincrone** casella di controllo.  
  
-   Per generare i tipi di contratto di messaggio in un client WCF, selezionare la **genera sempre contratti di messaggio** casella di controllo.  
  
-   Per specificare i tipi di raccolta elenco o dizionario per un client WCF, selezionare i tipi dal **tipo di raccolta** e **tipo di raccolta dizionario** Elenca.  
  
-   Per disabilitare la condivisione dei tipi, deselezionare il **Riutilizza tipi negli assembly di riferimento** casella di controllo. Per abilitare la condivisione di tipi per un subset di assembly di riferimento, selezionare la **Riutilizza tipi negli assembly di riferimento** caselle di controllo **Riutilizza tipi negli assembly di riferimento specificati**e selezionare il valore desiderato fa riferimento nel **elenco di assembly di riferimento**.  
  
## <a name="uielement-list"></a>Elenco UIElement  
 **Indirizzo**  
 Usato per aggiornare l'indirizzo Web in cui un riferimento al servizio cerca un servizio. Ad esempio, durante lo sviluppo il servizio potrebbe essere ospitato su un server di sviluppo, quindi spostato a un server di produzione, necessitando un cambio di indirizzo.  
  
> [!NOTE]
>  L'elemento Address non è disponibile quando il **Configura riferimento al servizio** verrà visualizzata la finestra di dialogo dalle **Add Service Reference Dialog Box**.  
  
 **Livello di accesso per classi generate**  
 Determina il livello di accesso del codice per le classi del client WCF.  
  
> [!NOTE]
>  Per i progetti di siti Web, questa opzione è impostata sempre su `Public` e non può essere modificata. Per altre informazioni, vedere [riferimenti al servizio di risoluzione dei problemi](../data-tools/troubleshooting-service-references.md).  
  
 **Genera operazioni asincrone**  
 Determina se i metodi del servizio WCF verranno chiamati in modo sincrono (impostazione predefinita) oppure asincrono.  
  
 **Genera operazioni basate su attività**  
 Durante la scrittura di codice asincrono, questa opzione consente di sfruttare la Task Parallel Library (TPL) introdotta con .Net 4. Visualizzare [Task Parallel Library (TPL)](http://msdn.microsoft.com/library/dd460717.aspx).  
  
 **Genera sempre contratti di messaggio**  
 Determina se i tipi di contratto di messaggio verranno generati per un client WCF. Per altre informazioni sui contratti di messaggio, vedere [Using Message Contracts](http://msdn.microsoft.com/library/1e19c64a-ae84-4c2f-9155-91c54a77c249).  
  
 **Tipo di raccolta**  
 Specifica il tipo di raccolta elenco per un client WCF. Il tipo predefinito è <xref:System.Array>.  
  
 **Tipo di raccolta dizionario**  
 Specifica il tipo di raccolta dizionario per un client WCF. Il tipo predefinito è <xref:System.Collections.Generic.Dictionary%602>.  
  
 **Riutilizza tipi negli assembly di riferimento**  
 Determina se un client WCF proverà a riusare i tipi già esistenti negli assembly di riferimento piuttosto di generare nuovi tipi quando un servizio viene aggiunto o aggiornato. Per impostazione predefinita, questa opzione è selezionata.  
  
 **Riutilizza tipi in tutti gli assembly di riferimento**  
 Quando selezionata, tutti i tipi di **elenco di assembly di riferimento** verranno riutilizzati, se possibile. Questa opzione è selezionata per impostazione predefinita.  
  
 **Riutilizza tipi negli assembly di riferimento specificati**  
 Se selezionata, solo i tipi selezionati nel **elenco di assembly di riferimento** verrà riutilizzato.  
  
 **Elenco assembly di riferimento**  
 Contiene un elenco di assembly di riferimento per il progetto o il sito Web. Quando **Riutilizza tipi negli assembly di riferimento specificati** è selezionata, può selezionare o deselezionare i singoli assembly.  
  
 **Aggiungi riferimento Web**  
 Consente di visualizzare il [NIB: finestra di dialogo riferimento Web Aggiungi](http://msdn.microsoft.com/en-us/bdf05776-c591-40af-bfd7-e1e2aa1e87b5).  
  
> [!NOTE]
>  Usare questa opzione solo per i progetti destinati alla versione 2.0 di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
> [!NOTE]
>  Il **Aggiungi riferimento Web** pulsante è disponibile solo quando il **Configura riferimento al servizio** verrà visualizzata la finestra di dialogo dal **Add Service Reference Dialog Box**.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: aggiungere, aggiornare o rimuovere un riferimento al servizio](http://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)   
 [Procedura: aggiungere un riferimento a un servizio Web](http://msdn.microsoft.com/library/952e49a1-567e-4a74-8cd7-f2e7b62c3168)   
 [Servizi Windows Communication Foundation e WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)

