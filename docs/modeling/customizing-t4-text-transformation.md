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
ms.openlocfilehash: 03acd2b989f3403c04d7a0bacdf1fb3e6e6213db
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251845"
---
# <a name="customize-t4-text-transformation"></a>Personalizzare la trasformazione del testo T4

I modelli di testo sono una funzionalità di Visual Studio che consente di generare codice programma o altri file di testo tramite un processo di trasformazione. Con [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]è possibile estendere il processo di trasformazione del modello predefinito personalizzando il processore di direttiva del modello di testo o l'host del modello di testo.

## <a name="in-this-section"></a>In questa sezione

 [Processo di trasformazione del modello di testo](../modeling/the-text-template-transformation-process.md) Viene descritto il funzionamento della trasformazione testo e viene illustrato il ruolo dell'host modello e dei processori di direttiva.

 [Creazione di processori di direttiva di modelli di testo T4 personalizzati](../modeling/creating-custom-t4-text-template-directive-processors.md) Il processore di direttiva gestisce le direttive nel modello, ad esempio `<#@template#>.` quando viene eseguito durante la compilazione del modello e può caricare assembly e altre risorse. Può inoltre inserire codice per caricare le risorse in fase di esecuzione. Definendo un processore di direttiva personalizzato, è possibile ridurre la complessità dei modelli.

 [Richiamo della trasformazione del testo in un'estensione di Visual](../modeling/invoking-text-transformation-in-a-vs-extension.md) Studio Se si scrive un'estensione di Visual Studio, ad esempio un comando di menu o un gestore eventi, l'estensione può usare il servizio modello di testo per trasformare qualsiasi modello di testo. È possibile passare i dati dei parametri nel modello usando l'oggetto sessione e ottenere i valori dall'interno del modello usando la `<#@parameter#>` direttiva.

 [Elaborazione di modelli di testo tramite un host personalizzato](../modeling/processing-text-templates-by-using-a-custom-host.md) Quando viene eseguito il codice del modello di testo, l'host fornisce l'accesso ai file esterni e allo stato dell'applicazione. L'host che esegue trasformazioni di testo in Visual Studio, ad esempio, può fornire l'accesso ai **Esplora soluzioni**. Vengono inoltre visualizzati errori nella finestra del messaggio di errore. Se si desidera eseguire trasformazioni di testo in un contesto diverso, è possibile definire un host personalizzato che fornisce l'accesso ai servizi disponibili in tale contesto.

 Se si scrive un'estensione di Visual Studio, è consigliabile utilizzare il servizio di trasformazione del testo esistente anziché scrivere un proprio host. Per altre informazioni, vedere [richiamo della trasformazione del testo in un'estensione di Visual](../modeling/invoking-text-transformation-in-a-vs-extension.md)Studio.

## <a name="reference"></a>Riferimenti

- [Scrivere un modello di testo T4](../modeling/writing-a-t4-text-template.md) fornisce la sintassi delle direttive e dei blocchi di controllo del modello di testo.