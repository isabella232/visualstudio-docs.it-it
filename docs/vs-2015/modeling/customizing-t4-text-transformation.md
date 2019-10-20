---
title: Personalizzazione della trasformazione del testo T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 71cec79acfcc934f9ddd910006f32f5207b26c84
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654960"
---
# <a name="customizing-t4-text-transformation"></a>Personalizzazione della trasformazione del testo T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I modelli di testo sono una funzionalità di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] che consentono di generare codice programma o altri file di testo tramite un processo di trasformazione. Utilizzando [!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)], è possibile estendere il processo di trasformazione del modello predefinito personalizzando il processore di direttiva del modello di testo o l'host del modello di testo.

## <a name="in-this-section"></a>Contenuto della sezione
 [Processo di trasformazione del modello di testo](../modeling/the-text-template-transformation-process.md) Viene descritto il funzionamento della trasformazione testo e viene illustrato il ruolo dell'host modello e dei processori di direttiva.

 [Creazione di processori di direttiva di modelli di testo T4 personalizzati](../modeling/creating-custom-t4-text-template-directive-processors.md) Il processore di direttiva gestisce le direttive nel modello, ad esempio `<#@template#>.` viene eseguito durante la compilazione del modello e può caricare assembly e altre risorse. Può inoltre inserire codice per caricare le risorse in fase di esecuzione. Definendo un processore di direttiva personalizzato, è possibile ridurre la complessità dei modelli.

 [Richiamo della trasformazione del testo in un'estensione di Visual](../modeling/invoking-text-transformation-in-a-vs-extension.md) Studio Se si scrive un'estensione [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ad esempio un comando di menu o un gestore eventi, l'estensione può usare il servizio modello di testo per trasformare qualsiasi modello di testo. È possibile passare i dati dei parametri nel modello usando l'oggetto sessione e ottenere i valori dall'interno del modello usando la direttiva `<#@parameter#>`.

 [Elaborazione di modelli di testo tramite un host personalizzato](../modeling/processing-text-templates-by-using-a-custom-host.md) Quando viene eseguito il codice del modello di testo, l'host fornisce l'accesso ai file esterni e allo stato dell'applicazione. Ad esempio, l'host che esegue trasformazioni di testo in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] può fornire l'accesso a Esplora soluzioni. Vengono inoltre visualizzati errori nella finestra del messaggio di errore. Se si desidera eseguire trasformazioni di testo in un contesto diverso, è possibile definire un host personalizzato che fornisce l'accesso ai servizi disponibili in tale contesto.

 Se si scrive un'estensione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], è consigliabile utilizzare il servizio di trasformazione del testo esistente anziché scrivere un proprio host. Per altre informazioni, vedere [richiamo della trasformazione del testo in un'estensione di Visual](../modeling/invoking-text-transformation-in-a-vs-extension.md)Studio.

## <a name="reference"></a>Reference
 [Scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md)

 Fornisce la sintassi delle direttive e dei blocchi di controllo del modello di testo.
