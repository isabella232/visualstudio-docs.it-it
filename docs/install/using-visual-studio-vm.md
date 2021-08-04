---
title: Uso di Visual Studio in una macchina virtuale di Azure
titleSuffix: ''
description: Informazioni su come usare Visual Studio in una macchina virtuale di Azure
ms.date: 11/17/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- azure services
- virtual machine
- installation
- visual studio
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 16cbe08f48d5d64d1213fb0422d2482f192309e8
ms.sourcegitcommit: 2430a38f23ac17b65dd8d3baa806e90433aba24f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/04/2021
ms.locfileid: "115094548"
---
# <a name="visual-studio-images-on-azure"></a>Immagini di Visual Studio in Azure

L'uso di Visual Studio in una macchina virtuale (VM) di Azure preconfigurata è un modo semplice e rapido per avere subito a disposizione un ambiente di sviluppo pienamente operativo. In [Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/apps/category/compute?filters=virtual-machine-images%3Bmicrosoft%3Bwindows&page=1&subcategories=application-infrastructure) sono disponibili immagini di sistema con diverse configurazioni di Visual Studio.

Non si è ancora provato Azure? [Creare un account Azure gratuito](https://azure.microsoft.com/free).

## <a name="what-configurations-and-versions-are-available"></a>Quali configurazioni e versioni sono disponibili?

Le immagini per le versioni principali più recenti, Visual Studio 2019, Visual Studio 2017 e Visual Studio 2015, sono disponibili in Azure Marketplace.  Per ogni versione principale sono elencate la versione originariamente rilasciata sul Web (RTW) e le versioni aggiornate più recenti.  Ognuna di queste versioni offre le edizioni Visual Studio Enterprise e Visual Studio Community.  Queste immagini vengono aggiornate almeno una volta al mese in modo da includere gli aggiornamenti più recenti per Visual Studio e Windows.  Anche se i nomi delle immagini rimangono invariati, la descrizione di ogni immagine include la versione del prodotto installato e la data corrente dell'immagine.

| Versione di rilascio                                                                                                                                                | Edizioni              | Versione del prodotto       |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------|-----------------------|
| [Visual Studio 2019: più recente (versione 16.8)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio2019latest?tab=Overview) | Enterprise, Community | Versione 16.8.0        |
| [Visual Studio 2019: RTW](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio2019?tab=Overview)                         | Enterprise            | Versione 16.0.20       |
| [Visual Studio 2017: Versione più recente (versione 15.9)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)           | Enterprise, Community | Versione 15.9.29       |
| [Visual Studio 2017: RTW](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)                             | Enterprise, Community | Versione 15.0.28       |
| [Visual Studio 2015: Versione più recente (aggiornamento 3)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)               | Enterprise, Community | Versione 14.0.25431.01 |

> [!NOTE]
> In base ai criteri di manutenzione di Microsoft, il supporto per la manutenzione della versione di Visual Studio 2015 originariamente rilasciata (RTW) è scaduto. Visual Studio 2015 Update 3 è l'unica versione rimanente offerta per la linea di prodotti Visual Studio 2015.

Per altre informazioni, vedere [Criteri di manutenzione di Visual Studio](/visualstudio/productinfo/vs-servicing-vs).

## <a name="what-features-are-installed"></a>Quali funzionalità vengono installate?

Ogni immagine contiene il set di funzionalità consigliato per una specifica edizione di Visual Studio. L'installazione include in genere i componenti seguenti:

* Tutti i carichi di lavoro disponibili, inclusi i componenti facoltativi consigliati per ogni carico di lavoro
* Targeting Pack, Strumenti di sviluppo ed SDK per .NET 4.6.2 e .NET 4.7
* Visual F#
* Estensione GitHub per Visual Studio
* Strumenti di LINQ to SQL

Per installare Visual Studio durante la creazione delle immagini viene usata la riga di comando seguente:

```shell
    vs_enterprise.exe --allWorkloads --includeRecommended --passive ^
       --add Microsoft.Net.Component.4.7.SDK ^
       --add Microsoft.Net.Component.4.7.TargetingPack ^
       --add Microsoft.Net.Component.4.6.2.SDK ^
       --add Microsoft.Net.Component.4.6.2.TargetingPack ^
       --add Microsoft.Net.ComponentGroup.4.7.DeveloperTools ^
       --add Microsoft.VisualStudio.Component.FSharp ^
       --add Component.GitHub.VisualStudio ^
       --add Microsoft.VisualStudio.Component.LinqToSql
```

Se le immagini non includono una funzionalità di Visual Studio che si ritiene necessaria, fornire commenti e suggerimenti tramite l'apposito strumento nell'angolo superiore destro della pagina.

## <a name="what-size-vm-should-i-choose"></a>Quale dimensione scegliere per la macchina virtuale?

Azure offre un'ampia gamma di macchine virtuali di diverse dimensioni. Poiché Visual Studio è una potente applicazione multithreading, è in genere necessaria una macchina virtuale con almeno due processori e 7 GB di memoria. Sono consigliate le dimensioni della macchina virtuale seguenti per le immagini di Visual Studio:

* Standard_D2_v3
* Standard_D2s_v3
* Standard_D4_v3
* Standard_D4s_v3
* Standard_D2_v2
* Standard_D2S_v2
* Standard_D3_v2

Per altre informazioni sulle dimensioni delle macchine virtuali più recenti, vedere [Dimensioni per le macchine virtuali Windows in Azure](/azure/virtual-machines/windows/sizes).

Con Azure è possibile optare per una soluzione diversa da quella iniziale ridimensionando la macchina virtuale. È possibile effettuare il provisioning di una nuova macchina virtuale con una dimensione più appropriata oppure ridimensionare la macchina virtuale esistente in base al diverso hardware sottostante. Per altre informazioni, vedere [Ridimensionare una VM Windows](/azure/virtual-machines/windows/resize-vm).

## <a name="after-the-vm-is-running-whats-next"></a>Che cosa si deve fare dopo che la macchina virtuale è in esecuzione?

Visual Studio segue il modello "Bring Your Own License" di Azure. Come per un'installazione in hardware proprietario, uno dei primi passaggi è quello di associare una licenza all'installazione di Visual Studio. Per sbloccare Visual Studio:

* Eseguire l'accesso con un account Microsoft associato a una sottoscrizione di Visual Studio
* Sbloccare Visual Studio usando il codice Product Key ottenuto con l'acquisto iniziale

Per altre informazioni, vedere [Accedere a Visual Studio](../ide/signing-in-to-visual-studio.md) e [Procedura: Sbloccare Visual Studio](../ide/how-to-unlock-visual-studio.md).

## <a name="how-do-i-save-the-development-vm-for-future-or-team-use"></a>Come si salva la macchina virtuale per lo sviluppo per un uso futuro o in team?

La gamma di ambienti di sviluppo è enorme e la configurazione di ambienti particolarmente complessi comporta costi notevoli. Indipendentemente dalla configurazione dell'ambiente, è possibile salvare o acquisire la macchina virtuale configurata come "immagine di base" per un uso futuro o per altri membri del proprio team. Quindi, all'avvio di una nuova macchina virtuale, è possibile effettuarne il provisioning dall'immagine di base anziché da quella di Azure Marketplace.

In sintesi, usare l'Utilità preparazione sistema (Sysprep) e arrestare la macchina virtuale in esecuzione, quindi acquisire *(figura 1)* la macchina virtuale come immagine tramite l'interfaccia utente del portale di Azure. Azure salva il file `.vhd` contenente l'immagine nell'account di archiviazione selezionato e la nuova immagine verrà quindi visualizzata come risorsa Immagine nell'elenco delle risorse della sottoscrizione.

![Acquisire un'immagine tramite l'interfaccia utente del portale di Azure](media/capture-vm.png)

*(Figura 1) Acquisire un'immagine tramite l'interfaccia utente del portale di Azure.*

Per altre informazioni, vedere [Creare un'immagine gestita di una macchina virtuale generalizzata in Azure](/azure/virtual-machines/windows/capture-image-resource).

> [!IMPORTANT]
> Non dimenticare di usare Sysprep per preparare la macchina virtuale. Se si omette questo passaggio, Azure non potrà effettuare il provisioning di una macchina virtuale in base a tale immagine.

> [!NOTE]
> L'archiviazione delle immagini comporta un costo incrementale che tuttavia può risultare insignificante rispetto ai costi generali da sostenere se ogni membro del team dovesse riconfigurare da zero la macchina virtuale. Ad esempio, a fronte di un costo di pochi euro, è possibile creare e archiviare per un mese un'immagine da 127 GB riutilizzabile dall'intero team. Tale costo è tuttavia trascurabile rispetto alle ore che ogni dipendente impiega per creare e convalidare una casella di sviluppo correttamente configurata per l'uso individuale.

Inoltre, le attività o le tecnologie di sviluppo possono richiedere maggiore scalabilità, ad esempio diverse configurazioni per l'ambiente di sviluppo e per le macchine virtuali. Per soddisfare queste esigenze, è possibile usare Azure DevTest Labs per creare _modelli_ che consentano di automatizzare la creazione di un'immagine finale. È possibile usare DevTest Labs anche per gestire i criteri per le macchine virtuali usate dal proprio team. L'articolo [Usare Azure DevTest Labs per sviluppatori](/azure/devtest-lab/devtest-lab-developer-lab) è la migliore fonte di informazioni su DevTest Labs.

## <a name="next-steps"></a>Passaggi successivi

Una volta acquisite le nozioni di base sulle immagini di Visual Studio preconfigurate, il passaggio successivo consiste nel creare una nuova macchina virtuale:

* [Creare una macchina virtuale Windows con il portale di Azure](/azure/virtual-machines/windows/quick-create-portal)
* [Panoramica di Macchine virtuali di Azure](/azure/virtual-machines/windows/overview)
