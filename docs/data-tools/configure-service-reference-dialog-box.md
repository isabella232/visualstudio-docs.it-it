---
title: Configura riferimento a servizio (finestra di dialogo)
description: Utilizzare la finestra di dialogo Configura riferimento al servizio in Visual Studio per configurare il comportamento dei servizi Windows Communication Foundation (WCF).
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 70faee4277625621074b1bd1bfdf667c818e1f46
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382351"
---
# <a name="configure-service-reference-dialog-box"></a>Configura riferimento a servizio (finestra di dialogo)

La finestra di dialogo **Configura riferimento al servizio** consente di configurare il comportamento dei servizi Windows Communication Foundation (WCF).

Per accedere alla finestra di dialogo **Configura riferimento a servizio** , fare clic con il pulsante destro del mouse su un riferimento al servizio in **Esplora soluzioni** e scegliere **Configura riferimento a servizio**. È anche possibile accedere alla finestra di dialogo facendo clic sul pulsante **Avanzate** nella **finestra di dialogo Aggiungi riferimento al servizio**.

## <a name="task-list"></a>Elenco attività

- Per cambiare l'indirizzo al quale è ospitato il servizio WCF, immettere il nuovo indirizzo nel campo **Indirizzo**.

- Per cambiare il livello di accesso alle classi in un client WCF, selezionare una parola chiave del livello di accesso nell'elenco **Livello di accesso per classi generate**.

- Per chiamare i metodi di un servizio WCF in modo asincrono, selezionare la casella di controllo **Genera operazioni asincrone**.

- Per generare i tipi di contratto di messaggio in un client WCF, selezionare la casella di controllo **Genera sempre contratti di messaggio**.

- Per specificare i tipi di raccolta elenco o dizionario per un client WCF, selezionare i tipi dagli elenchi **Tipo di raccolta** e **Tipo di raccolta dizionario**.

- Per disabilitare la condivisione dei tipi, deselezionare la casella di controllo **Riutilizza tipi in assembly di riferimento**. Per abilitare la condivisione di tipi per un sottoinsieme di assembly di riferimento, selezionare la casella di controllo **Riutilizza tipi in assembly di riferimento** , selezionare **Riutilizza tipi negli assembly di riferimento specificati** e selezionare i riferimenti desiderati nell'elenco **Assembly di riferimento**.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia

**Indirizzo**

Aggiorna l'indirizzo Web in cui un riferimento al servizio Cerca un servizio. Ad esempio, durante lo sviluppo, il servizio può essere ospitato in un server di sviluppo e successivamente spostato in un server di produzione, rendendo necessario un cambio di indirizzo.

> [!NOTE]
> L'elemento Address non è disponibile quando viene visualizzata la finestra di dialogo **Configura riferimento a servizio** dalla **finestra di dialogo Aggiungi riferimento al servizio**.

**Livello di accesso per classi generate**

Determina il livello di accesso del codice per le classi del client WCF.

> [!NOTE]
> Per i progetti di siti Web, questa opzione è impostata sempre su `Public` e non può essere modificata. Per altre informazioni, vedere [Risoluzione dei problemi relativi ai riferimenti al servizio](../data-tools/troubleshooting-service-references.md).

**Genera operazioni asincrone**

Determina se i metodi del servizio WCF vengono chiamati in modo sincrono (impostazione predefinita) o in modo asincrono.

**Genera operazioni basate su attività**

Quando si scrive codice asincrono, questa opzione consente di sfruttare i vantaggi della Task Parallel Library (TPL) introdotta con .NET 4. Vedere [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl).

**Genera sempre contratti di messaggio**

Determina se i tipi di contratto di messaggio vengono generati per un client WCF. Per altre informazioni sui contratti di messaggio, vedere [Uso dei contratti di messaggio](/dotnet/framework/wcf/feature-details/using-message-contracts).

**Tipo di raccolta**

Specifica il tipo di raccolta elenco per un client WCF. Il tipo predefinito è <xref:System.Array>.

**Tipo di raccolta dizionario**

Specifica il tipo di raccolta dizionario per un client WCF. Il tipo predefinito è <xref:System.Collections.Generic.Dictionary%602>.

**Riutilizza tipi in assembly di riferimento**

Determina se un client WCF tenta di riutilizzare ciò che esiste già negli assembly a cui si fa riferimento anziché generare nuovi tipi quando un servizio viene aggiunto o aggiornato. Per impostazione predefinita, questa opzione è selezionata.

**Riutilizza tipi in tutti gli assembly di riferimento**

Quando questa opzione è selezionata, tutti i tipi nell' **elenco degli assembly a cui si fa riferimento** vengono riutilizzati, se possibile. Questa opzione è selezionata per impostazione predefinita.

**Riutilizza tipi negli assembly di riferimento specificati**

Quando questa opzione è selezionata, vengono riutilizzati solo i tipi selezionati nell' **elenco degli assembly a cui si fa riferimento** .

**Elenco Assembly di riferimento**

Contiene un elenco di assembly di riferimento per il progetto o il sito Web. Quando si seleziona **Riutilizza tipi in assembly di riferimento specificati** , è possibile selezionare o deselezionare singoli assembly.

**Aggiungi riferimento Web**

Visualizza la **finestra di dialogo Aggiungi riferimento Web**.

> [!NOTE]
> Questa opzione deve essere usata solo per i progetti destinati alla versione 2,0 della .NET Framework.
>
> [!NOTE]
> Il pulsante **Aggiungi riferimento Web** è disponibile solo quando nella finestra di dialogo **Aggiungi riferimento al servizio** viene visualizzata la finestra di dialogo **Configura riferimento al servizio** .

## <a name="see-also"></a>Vedere anche

- [Procedura: Aggiungere un riferimento a un servizio Web](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Servizi Windows Communication Foundation e WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)
