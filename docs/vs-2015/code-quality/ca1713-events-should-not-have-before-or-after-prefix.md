---
title: 'CA1713: gli eventi non devono avere il prefisso Before o After | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b05c39a9d8a4a004359baf63919eb427c25fa5d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543962"
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713: Non usare il prefisso Before o After negli eventi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|
|CheckId|CA1713|
|Category|Microsoft. Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Il nome di un evento inizia con ' before ' o ' after '.

## <a name="rule-description"></a>Descrizione della regola
 I nomi degli eventi devono descrivere l'azione che genera l'evento. Per denominare eventi correlati generati in una sequenza specifica, utilizzare i tempi verbali presente o passato per indicare la posizione relativa nella sequenza di azioni. Ad esempio, quando si denomina una coppia di eventi generata quando si chiude una risorsa, è possibile denominarla ' closing ' è Closed ' anziché' BeforeClose ' è AfterClose '.

 Le convenzioni di denominazione forniscono un aspetto comune per le librerie destinate al Common Language Runtime. In questo modo si riduce la curva di apprendimento necessaria per le nuove librerie software e si aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente esperto nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rimuovere il prefisso dal nome dell'evento e provare a modificare il nome in modo da usare il tempo presente o passato di un verbo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.
