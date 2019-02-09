---
title: Personalizzazione della trasformazione del testo T4
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33f7fd14ff62369de66e4934bf9bb2cf6fd83542
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55951553"
---
# <a name="customize-t4-text-transformation"></a>Personalizzare la trasformazione del testo T4

Modelli di testo sono una funzionalità di Visual Studio che consentono di generare codice programma o altri file di testo tramite un processo di trasformazione. Usando [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)], è possibile estendere il processo di trasformazione del modello predefinito personalizzando il processore di direttiva del modello di testo o l'host del modello di testo.

## <a name="in-this-section"></a>In questa sezione

 [Il processo di trasformazione del modello di testo](../modeling/the-text-template-transformation-process.md) viene descritto il funzionamento di trasformazione del testo e spiega il ruolo di host del modello e i processori di direttiva.

 [Creazione di processori di direttiva modello di testo T4 personalizzati](../modeling/creating-custom-t4-text-template-directive-processors.md) processore di direttiva riguarda le direttive nel modello, ad esempio `<#@template#>.` viene eseguito durante la compilazione del modello e può caricare assembly e altre risorse. Inoltre possibile inserire il codice che caricherà le risorse in fase di esecuzione. Definendo il proprio processore di direttiva, è possibile ridurre la complessità dei modelli.

 [Richiamo della trasformazione del testo in un'estensione VS](../modeling/invoking-text-transformation-in-a-vs-extension.md) se si sta scrivendo un'estensione di Visual Studio, ad esempio un gestore di evento o di comando di menu, l'estensione può utilizzare il servizio del modello di testo per trasformare qualsiasi modello di testo. È possibile passare i dati dei parametri nel modello tramite l'oggetto sessione e ottenere i valori all'interno del modello usando il `<#@parameter#>` direttiva.

 [L'elaborazione di modelli di testo tramite un Host personalizzato](../modeling/processing-text-templates-by-using-a-custom-host.md) quando viene eseguito il codice del modello di testo, l'host fornisce l'accesso a file esterni e lo stato dell'applicazione. Ad esempio, l'host che esegue le trasformazioni di testo in Visual Studio possa fornire l'accesso a **Esplora soluzioni**. Inoltre, verranno visualizzati errori nella finestra di messaggio di errore. Se si desidera eseguire le trasformazioni di testo in un contesto diverso, è possibile definire il proprio host che consente di accedere ai servizi disponibili in tale contesto.

 Se si sta scrivendo un'estensione di Visual Studio, è consigliabile usare il servizio di trasformazione di testo esistente invece di scrivere il proprio host. Per altre informazioni, vedere [richiamo di trasformazione del testo in un'estensione VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Riferimenti

- [Scrivere un modello di testo T4](../modeling/writing-a-t4-text-template.md) fornisce la sintassi delle direttive di modello di testo e blocchi di controllo.