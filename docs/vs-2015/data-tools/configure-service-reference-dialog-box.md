---
title: Finestra di dialogo Configura riferimento al servizio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac8f4cf619bbdd007bb7aa570f549ae3c0b50e86
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651106"
---
# <a name="configure-service-reference-dialog-box"></a>Configura riferimento a servizio (finestra di dialogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La finestra di dialogo **Configura riferimento al servizio** consente di configurare il comportamento dei [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] servizi.

> [!NOTE]
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere Importa/esporta impostazioni dal menu Strumenti. Per altre informazioni, vedere [personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Per accedere alla finestra di dialogo **Configura riferimento a servizio**, fare clic con il pulsante destro del mouse su un riferimento al servizio in **Esplora soluzioni** e scegliere **Configura riferimento a servizio**. È anche possibile accedere alla finestra di dialogo facendo clic sul pulsante **Avanzate** nella **finestra di dialogo Aggiungi riferimento al servizio**.

## <a name="task-list"></a>Elenco attività

- Per cambiare l'indirizzo al quale è ospitato il servizio WCF, immettere il nuovo indirizzo nel campo **Indirizzo**.

- Per cambiare il livello di accesso alle classi in un client WCF, selezionare una parola chiave del livello di accesso nell'elenco **Livello di accesso per classi generate**.

- Per chiamare i metodi di un servizio WCF in modo asincrono, selezionare la casella di controllo **Genera operazioni asincrone**.

- Per generare i tipi di contratto di messaggio in un client WCF, selezionare la casella di controllo **Genera sempre contratti di messaggio**.

- Per specificare i tipi di raccolta elenco o dizionario per un client WCF, selezionare i tipi dagli elenchi **Tipo di raccolta** e **Tipo di raccolta dizionario**.

- Per disabilitare la condivisione dei tipi, deselezionare la casella di controllo **Riutilizza tipi in assembly di riferimento**. Per abilitare la condivisione di tipi per un sottoinsieme di assembly di riferimento, selezionare la casella di controllo **Riutilizza tipi in assembly di riferimento**, selezionare **Riutilizza tipi negli assembly di riferimento specificati** e selezionare i riferimenti desiderati nell'elenco **Assembly di riferimento**.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia
 **Indirizzo** Usato per aggiornare l'indirizzo Web in cui un riferimento al servizio Cerca un servizio. Ad esempio, durante lo sviluppo il servizio potrebbe essere ospitato su un server di sviluppo, quindi spostato a un server di produzione, necessitando un cambio di indirizzo.

> [!NOTE]
> L'elemento Address non è disponibile quando viene visualizzata la finestra di dialogo **Configura riferimento a servizio** dalla **finestra di dialogo Aggiungi riferimento al servizio**.

 **Livello di accesso per le classi generate** Determina il livello di accesso al codice per le classi client WCF.

> [!NOTE]
> Per i progetti di siti Web, questa opzione è impostata sempre su `Public` e non può essere modificata. Per ulteriori informazioni, vedere [risoluzione dei problemi relativi ai riferimenti al servizio](../data-tools/troubleshooting-service-references.md).

 **Genera operazioni asincrone** Determina se i metodi del servizio WCF verranno chiamati in modo sincrono (impostazione predefinita) o in modo asincrono.

 **Genera operazioni basate su attività** Quando si scrive codice asincrono, questa opzione consente di sfruttare i vantaggi della Task Parallel Library (TPL) introdotta con .NET 4. Vedere [Task Parallel Library (TPL)](https://msdn.microsoft.com/library/dd460717.aspx).

 **Genera sempre contratti di messaggio** Determina se i tipi di contratto di messaggio verranno generati per un client WCF. Per ulteriori informazioni sui contratti di messaggio, vedere [utilizzo dei contratti di messaggio](https://msdn.microsoft.com/library/1e19c64a-ae84-4c2f-9155-91c54a77c249).

 **Tipo di raccolta** Specifica il tipo di raccolta di elenchi per un client WCF. Il tipo predefinito è <xref:System.Array>.

 **Tipo di raccolta dizionario** Specifica il tipo di raccolta dizionario per un client WCF. Il tipo predefinito è <xref:System.Collections.Generic.Dictionary%602>.

 **Riutilizza tipi negli assembly a cui si fa riferimento** Determina se un client WCF tenterà di riutilizzare già esistente negli assembly a cui si fa riferimento anziché generare nuovi tipi quando viene aggiunto o aggiornato un servizio. Per impostazione predefinita, questa opzione è selezionata.

 **Riutilizza tipi in tutti gli assembly a cui si fa riferimento** Quando questa opzione è selezionata, se possibile verranno riutilizzati tutti i tipi nell' **elenco degli assembly a cui si fa riferimento** . Questa opzione è selezionata per impostazione predefinita.

 **Riutilizza tipi negli assembly a cui si fa riferimento specificati** Quando questa opzione è selezionata, verranno riutilizzati solo i tipi selezionati nell' **elenco assembly a cui si fa riferimento** .

 **Elenco assembly di riferimento** Contiene un elenco di assembly di riferimento per il progetto o il sito Web. Quando si seleziona **Riutilizza tipi negli assembly di riferimento specificati** , è possibile selezionare o deselezionare singoli assembly.

 **Aggiungi riferimento Web** Visualizza la finestra di [dialogo penne: Aggiungi riferimento Web](https://msdn.microsoft.com/bdf05776-c591-40af-bfd7-e1e2aa1e87b5).

> [!NOTE]
> Usare questa opzione solo per i progetti destinati alla versione 2.0 di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

> [!NOTE]
> Il pulsante **Aggiungi riferimento Web** è disponibile solo quando nella finestra di dialogo **Aggiungi riferimento al servizio**viene visualizzata la finestra di dialogo **Configura riferimento al servizio** .

## <a name="see-also"></a>Vedere anche
 [Procedura: aggiungere, aggiornare o rimuovere un riferimento al servizio](https://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9) [procedura: aggiungere un riferimento a un servizio Web](https://msdn.microsoft.com/library/952e49a1-567e-4a74-8cd7-f2e7b62c3168) [Windows Communication Foundation servizi e WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)
