---
title: Configura riferimento a servizio (finestra di dialogo)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f1b2c37f551bf7b5e0a781b91420881c594ade68
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180464"
---
# <a name="configure-service-reference-dialog-box"></a>Configura riferimento a servizio (finestra di dialogo)

Il **Configura riferimento al servizio** nella finestra di dialogo consente di configurare il comportamento dei servizi Windows Communication Foundation (WCF).

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

Per l'accesso di **Configura riferimento al servizio** della finestra di dialogo scelta di un servizio fa riferimento nel **Esplora soluzioni** e scegliere **Configura riferimento al servizio**. È anche possibile accedere nella finestra di dialogo facendo clic la **avanzate** pulsante il **Add Service Reference Dialog Box**.

## <a name="task-list"></a>Elenco attività

- Per modificare l'indirizzo in cui è ospitato un servizio WCF, immettere il nuovo indirizzo nella **indirizzo** campo.

- Per modificare il livello di accesso per le classi in un client WCF, selezionare una parola chiave a livello di accesso nel **livello di accesso per classi generate** elenco.

- Per chiamare i metodi di un servizio WCF in modo asincrono, selezionare la **Genera operazioni asincrone** casella di controllo.

- Per generare i tipi di contratto di messaggio in un client WCF, selezionare la **genera sempre contratti di messaggio** casella di controllo.

- Per specificare i tipi di raccolta elenco o dizionario per un client WCF, selezionare i tipi dal **tipo di raccolta** e **tipo di raccolta dizionario** Elenca.

- Per disabilitare la condivisione dei tipi, deselezionare il **Riutilizza tipi negli assembly di riferimento** casella di controllo. Per abilitare la condivisione di tipi per un subset di assembly di riferimento, selezionare la **Riutilizza tipi negli assembly di riferimento** caselle di controllo **Riutilizza tipi negli assembly di riferimento specificati**e selezionare il valore desiderato fa riferimento nel **elenco di assembly di riferimento**.

## <a name="uielement-list"></a>Elenco UIElement

 **Indirizzo**

 Aggiorna l'indirizzo web in cui un riferimento al servizio cerca un servizio. Ad esempio, durante lo sviluppo, il servizio può essere ospitato in un server di sviluppo e in seguito spostato in un server di produzione, è necessario eseguire un cambio di indirizzo.

> [!NOTE]
> L'elemento Address non è disponibile quando il **Configura riferimento al servizio** verrà visualizzata la finestra di dialogo dalle **Add Service Reference Dialog Box**.

 **Livello di accesso per classi generate**

 Determina il livello di accesso del codice per le classi del client WCF.

> [!NOTE]
> Per i progetti di siti Web, questa opzione è impostata sempre su `Public` e non può essere modificata. Per altre informazioni, vedere [risoluzione dei riferimenti al servizio](../data-tools/troubleshooting-service-references.md).

 **Genera operazioni asincrone**

 Determina se i metodi del servizio WCF viene chiamato in modo sincrono (impostazione predefinita) o in modo asincrono.

 **Genera operazioni basate su attività**

 Quando si scrive codice asincrono, questa opzione consente di sfruttare i vantaggi della Task Parallel Library (TPL) introdotta con .NET 4. Visualizzare [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl).

 **Genera sempre contratti di messaggio**

 Determina se i tipi di contratto di messaggio sono generati per un client WCF. Per altre informazioni sui contratti di messaggio, vedere [tramite i contratti di messaggio](/dotnet/framework/wcf/feature-details/using-message-contracts).

 **Tipo di raccolta**

 Specifica il tipo di raccolta elenco per un client WCF. Il tipo predefinito è <xref:System.Array>.

 **Tipo di raccolta dizionario**

 Specifica il tipo di raccolta dizionario per un client WCF. Il tipo predefinito è <xref:System.Collections.Generic.Dictionary%602>.

 **Riutilizza tipi negli assembly di riferimento**

 Determina se un client WCF tenta di riutilizzare elementi esistenti in assembly di riferimento invece di generare nuovi tipi quando un servizio viene aggiunto o aggiornato. Per impostazione predefinita, questa opzione è selezionata.

 **Riutilizza tipi in tutti gli assembly di riferimento**

 Quando selezionata, tutti i tipi di **elenco di assembly di riferimento** vengono riutilizzati, se possibile. Questa opzione è selezionata per impostazione predefinita.

 **Riutilizza tipi negli assembly di riferimento specificati**

 Se selezionata, solo i tipi selezionati nel **elenco di assembly di riferimento** vengono riutilizzati.

 **Elenco assembly di riferimento**

 Contiene un elenco di assembly di riferimento per il progetto o sito Web. Quando si seleziona **Riutilizza tipi negli assembly di riferimento specificati**, è possibile selezionare o deselezionare singoli assembly.

 **Aggiungi riferimento Web**

 Consente di visualizzare il **Aggiungi riferimento Web** nella finestra di dialogo.

> [!NOTE]
> Questa opzione deve essere utilizzata solo per i progetti destinati alla versione 2.0 il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

> [!NOTE]
> Il **Aggiungi riferimento Web** pulsante è disponibile solo quando il **Configura riferimento al servizio** verrà visualizzata la finestra di dialogo dal **Add Service Reference Dialog Box**.

## <a name="see-also"></a>Vedere anche

- [Procedura: aggiungere un riferimento a un servizio web](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Servizi Windows Communication Foundation e WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)