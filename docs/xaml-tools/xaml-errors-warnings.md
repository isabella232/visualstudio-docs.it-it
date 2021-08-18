---
title: Errori e avvisi XAML
description: Informazioni su errori e avvisi XAML in Visual Studio, tra cui come vengono classificati gli errori, come ottenere informazioni sugli errori e come trovare le opzioni per correggerli.
ms.custom: SEO-VS-2020
ms.date: 03/06/2018
ms.topic: error-reference
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.workload:
- multiple
ms.openlocfilehash: f164a002b5e2c221a10cade55c50fef120452ab6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122098814"
---
# <a name="xaml-errors-and-warnings"></a>Errori e avvisi XAML

Durante la creazione di codice XAML, Visual Studio analizza il codice mentre lo si digita. Quando viene rilevato un errore in una riga di codice, viene visualizzata una sottolineatura ondulata. Se si porta il cursore del mouse sulla sottolineatura, vengono visualizzate informazioni sull'errore o sull'avviso. Per alcuni errori e avvisi, viene visualizzata una lampadina di Azione rapida e si usa + **CTRL.** consente di visualizzare le opzioni per la risoluzione del problema.

## <a name="error-types"></a>Tipi di errore

Vari strumenti analizzano il codice XAML in background. Gli errori XAML sono suddivisi nei tre tipi seguenti, a seconda dello strumento che ha rilevato l'errore:

|**Errore rilevato da**|**Formato codice di errore**|**Visual Studio Versione**|
| - |-----------------| - |
|Servizio di linguaggio XAML (Editor XAML)|XLSxxxx| Tutte le versioni |
|XAML Designer|XDGxxxx| Tutte le versioni | 
|Modifica e continuazione per XAML|XECxxxx| Visual Studio 2019 versione 16.1 o precedente |
|Ricaricamento rapido XAML | XHRxxxx | Visual Studio 2019 versione 16.2 o successiva |

Per altri dettagli sul rebranding di Modifica XAML & continua come Ricaricamento rapido XAML, vedi le note [sulla versione](/visualstudio/releases/2019/release-notes-v16.2#wpfuwp-tooling)

> [!Note]
> Non tutti gli errori o avvisi hanno un codice corrispondente. Gli errori senza codice sono in genere errori della finestra di progettazione XAML.

## <a name="suppress-xaml-designer-errors"></a>Eliminare gli errori della finestra di progettazione XAML

Aprire la finestra di dialogo **Opzioni** selezionando **Strumenti > Opzioni** e selezionare **Editor di testo > XAML > Varie**.

Deselezionare la casella di controllo **Show errors detected by the XAML designer** (Visualizza errori rilevati dalla finestra di progettazione XAML).

![Eliminare gli errori della finestra di progettazione XAML](media/suppress_xaml_designer_errors.png)