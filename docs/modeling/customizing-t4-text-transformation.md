---
title: Personalizzazione della trasformazione del testo T4
description: Informazioni su come estendere il processo di trasformazione del modello predefinito personalizzando il processore di direttiva del modello di testo o l'host del modello di testo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 35942b5f87458d1ccaf4892d33b5bba1dcdbb8a0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389358"
---
# <a name="customize-t4-text-transformation"></a>Personalizzare la trasformazione del testo T4

I modelli di testo sono una funzionalità Visual Studio che consentono di generare codice programma o altri file di testo tramite un processo di trasformazione. Usando , è possibile estendere il processo di trasformazione del modello predefinito personalizzando il processore di direttiva del modello di testo o [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] l'host del modello di testo.

## <a name="in-this-section"></a>Contenuto della sezione

 [Processo di trasformazione del modello di testo](../modeling/the-text-template-transformation-process.md) Viene descritto il funzionamento della trasformazione del testo e viene illustrato il ruolo dell'host del modello e dei processori di direttiva.

 [Creazione di processori di direttiva del modello di testo T4 personalizzati](../modeling/creating-custom-t4-text-template-directive-processors.md) Il processore di direttiva gestisce le direttive nel modello, ad esempio viene eseguito durante la compilazione del modello e può caricare `<#@template#>.` assembly e altre risorse. Può anche inserire codice che carica le risorse in fase di esecuzione. Definendo un processore di direttiva personalizzato, è possibile ridurre la complessità dei modelli.

 [Chiamata della trasformazione Testo in un'estensione di Visual Studio](../modeling/invoking-text-transformation-in-a-vs-extension.md) Se si scrive un'estensione Visual Studio, ad esempio un comando di menu o un gestore eventi, l'estensione può usare il servizio Templating di testo per trasformare qualsiasi modello di testo. È possibile passare i dati dei parametri al modello usando l'oggetto Session e ottenere i valori dall'interno del modello usando la `<#@parameter#>` direttiva .

 [Elaborazione di modelli di testo tramite un host personalizzato](../modeling/processing-text-templates-by-using-a-custom-host.md) Quando viene eseguito il codice del modello di testo, l'host fornisce l'accesso ai file esterni e allo stato dell'applicazione. Ad esempio, l'host che esegue trasformazioni di testo in Visual Studio può fornire l'accesso **a Esplora soluzioni**. Visualizza anche gli errori nella finestra del messaggio di errore. Se si desidera eseguire trasformazioni di testo in un contesto diverso, è possibile definire un host personalizzato che fornisce l'accesso ai servizi disponibili in tale contesto.

 Se si scrive un'estensione Visual Studio, è consigliabile usare il servizio di trasformazione testo esistente invece di scrivere un host personalizzato. Per altre informazioni, vedere [Chiamata della trasformazione testo in un'estensione di Visual Studio.](../modeling/invoking-text-transformation-in-a-vs-extension.md)

## <a name="reference"></a>Riferimento

- [Scrivere un modello di testo T4 fornisce](../modeling/writing-a-t4-text-template.md) la sintassi delle direttive del modello di testo e dei blocchi di controllo.
