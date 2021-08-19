---
title: Confronto tra VBA e Office soluzioni Visual Studio
description: Informazioni sulle differenze tra Microsoft Visual Basic, Applications Edition (VBA) e Microsoft Office soluzioni Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c1ba6753c28bae5094e83f28be72632f25b82f7b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147661"
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Confronto tra VBA e Office soluzioni Visual Studio
  In Microsoft Visual Basic, Applications Edition (VBA) viene usato codice non gestito che è strettamente integrato con le applicazioni di Office. I progetti di Microsoft Office creati tramite Visual Studio consentono di sfruttare gli strumenti di progettazione di Visual Studio e .NET Framework.

 Per informazioni sui tipi di soluzioni Office che è possibile creare usando Visual Studio, vedere Office panoramica dello sviluppo di [soluzioni &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="comparison"></a>Confronto
 Nella tabella riportata di seguito viene fornito un confronto di base tra soluzioni VBA e soluzioni Office in Visual Studio.

|Soluzioni VBA|Soluzioni Office in Visual Studio|
|-------------------|---------------------------------------|
|Utilizzano codice connesso al documento specifico e con cui viene conservato.|Usa il codice archiviato separatamente dal documento (per le personalizzazioni a livello di documento) o in un assembly caricato dall'applicazione (per VSTO componenti aggiuntivi).|
|Funzionano con i modelli a oggetti di Office e con le API di VBA.|Forniscono accesso ai modelli a oggetti di Office e alle API di [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .|
|Progettate per la registrazione di macro e per un'esperienza di sviluppo semplificata.|Progettate per garantire sicurezza, una gestione facilitata del codice e la possibilità di usare l'intero ambiente di sviluppo integrato di Visual Studio.|
|Funziona bene per le soluzioni che traggono vantaggio da una stretta integrazione con Office applicazioni.|Particolarmente adatte per soluzioni che sfruttano le risorse complete di Visual Studio e [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].|
|Presentano funzionalità limitate per le soluzioni aziendali, soprattutto in relazione alla sicurezza e alla distribuzione.|Progettate per le aziende.|

 Alcune operazioni possono essere eseguite rapidamente con maggiore semplicità usando VBA. In particolare, può rivelarsi utile continuare a usare VBA per:

- Funzioni dei fogli di lavoro personalizzate.

- Registrazione di macro.

## <a name="combine-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>Combinare soluzioni VBA e Office soluzioni create usando Visual Studio
 È possibile chiamare codice VBA dalle soluzioni Office create tramite Visual Studio ed è anche possibile chiamare codice delle soluzioni Office create tramite Visual Studio da VBA. La tecnica specifica differisce a seconda del fatto che la soluzione Office sia un componente aggiuntivo VSTO o una personalizzazione a livello di documento. Per altre informazioni, vedere Chiamare codice [in](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) VSTO componenti aggiuntivi da altre soluzioni Office e [Combinare le personalizzazioni VBA](../vsto/combining-vba-and-document-level-customizations.md)e a livello di documento.

## <a name="see-also"></a>Vedi anche
- [Office panoramica dello sviluppo di soluzioni &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Chiamare il codice VSTO componenti aggiuntivi da altre Office soluzioni](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Combinare le personalizzazioni VBA e a livello di documento](../vsto/combining-vba-and-document-level-customizations.md)
- [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md)
- [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)
- [Introduzione allo &#40;Office sviluppo in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
