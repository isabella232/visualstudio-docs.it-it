---
title: Errori e avvisi XAML
description: Informazioni sugli errori e gli avvisi XAML in Visual Studio, incluse le modalità di classificazione degli errori, su come ottenere informazioni sugli errori e su come trovare le opzioni per correggerle.
ms.custom: SEO-VS-2020
ms.date: 03/06/2018
ms.topic: error-reference
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3b0c785bef80f59c165f251b2986f0db1eb8bc63
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414477"
---
# <a name="xaml-errors-and-warnings"></a>Errori e avvisi XAML

Durante la creazione di codice XAML, Visual Studio analizza il codice mentre lo si digita. Quando viene rilevato un errore in una riga di codice, viene visualizzata una sottolineatura ondulata. Se si porta il cursore del mouse sulla sottolineatura, vengono visualizzate informazioni sull'errore o sull'avviso. Per alcuni errori e avvisi, viene visualizzata una lampadina con azione rapida e viene usato il **tasto CTRL** + **.** consente di visualizzare le opzioni per la risoluzione del problema.

## <a name="error-types"></a>Tipi di errore

Vari strumenti analizzano il codice XAML in background. Gli errori XAML sono suddivisi nei tre tipi seguenti, a seconda dello strumento che ha rilevato l'errore:

|**Errore rilevato da**|**Formato codice di errore**|**Versione di Visual Studio**|
| - |-----------------| - |
|Servizio di linguaggio XAML (Editor XAML)|XLSxxxx| Tutte le versioni |
|XAML Designer|XDGxxxx| Tutte le versioni | 
|Modifica e continuazione per XAML|XECxxxx| Visual Studio 2019 versione 16,1 o precedente |
|Ricaricamento rapido XAML | XHRxxxx | Visual Studio 2019 versione 16,2 o successiva |

Per altri dettagli sulla nuova personalizzazione della modifica XAML & continuare a eseguire il ricaricamento a caldo di XAML, vedere le [Note sulla versione](/visualstudio/releases/2019/release-notes-v16.2#wpfuwp-tooling)

> [!Note]
> Non tutti gli errori o avvisi hanno un codice corrispondente. Gli errori senza codice sono in genere errori della finestra di progettazione XAML.

## <a name="suppress-xaml-designer-errors"></a>Eliminare gli errori della finestra di progettazione XAML

Aprire la finestra di dialogo **Opzioni** selezionando **Strumenti > Opzioni** e selezionare **Editor di testo > XAML > Varie**.

Deselezionare la casella di controllo **Show errors detected by the XAML designer** (Visualizza errori rilevati dalla finestra di progettazione XAML).

![Eliminare gli errori della finestra di progettazione XAML](media/suppress_xaml_designer_errors.png)