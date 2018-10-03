---
title: Personalizzazione della trasformazione del testo T4 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e304b38979b80c1d67d3f88accdbfa584406c9cb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532608"
---
# <a name="customizing-t4-text-transformation"></a>Personalizzazione della trasformazione del testo T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [personalizzazione di trasformazione del testo T4](https://docs.microsoft.com/visualstudio/modeling/customizing-t4-text-transformation).  
  
Modelli di testo sono una funzionalità di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] che consentono di generare codice programma o altri file di testo tramite un processo di trasformazione. Usando [!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)], è possibile estendere il processo di trasformazione del modello predefinito personalizzando il processore di direttiva del modello di testo o l'host del modello di testo.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Processo di trasformazione del modello di testo](../modeling/the-text-template-transformation-process.md)  
 Viene descritto il funzionamento di trasformazione del testo e spiega il ruolo di host del modello e i processori di direttiva.  
  
 [Creazione di processori di direttiva di modelli di testo T4 personalizzati](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Il processore di direttiva riguarda le direttive nel modello, ad esempio `<#@template#>.` viene eseguito durante la compilazione del modello e può caricare assembly e altre risorse. Inoltre possibile inserire il codice che caricherà le risorse in fase di esecuzione. Definendo il proprio processore di direttiva, è possibile ridurre la complessità dei modelli.  
  
 [Richiamo della trasformazione del testo in un'estensione VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 Se si sta scrivendo un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] estensione, ad esempio un gestore di evento o di comando di menu, l'estensione può utilizzare il servizio del modello di testo per trasformare qualsiasi modello di testo. È possibile passare i dati dei parametri nel modello tramite l'oggetto sessione e ottenere i valori all'interno del modello usando il `<#@parameter#>` direttiva.  
  
 [Elaborazione di modelli di testo tramite un host personalizzato](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 Quando viene eseguito il codice del modello di testo, l'host fornisce l'accesso a file esterni e lo stato dell'applicazione. Ad esempio, l'host che esegue le trasformazioni di testo in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] può fornire l'accesso a Esplora soluzioni. Inoltre, verranno visualizzati errori nella finestra di messaggio di errore. Se si desidera eseguire le trasformazioni di testo in un contesto diverso, è possibile definire il proprio host che consente di accedere ai servizi disponibili in tale contesto.  
  
 Se si sta scrivendo un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] estensione, è consigliabile usare il servizio di trasformazione di testo esistente invece di scrivere il proprio host. Per altre informazioni, vedere [richiamo di trasformazione del testo in un'estensione VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## <a name="reference"></a>Riferimenti  
 [Scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md)  
  
 Fornisce la sintassi delle direttive di modello di testo e blocchi di controllo.



