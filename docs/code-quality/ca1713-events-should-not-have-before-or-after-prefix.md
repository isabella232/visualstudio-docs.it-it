---
title: 'CA1713: Non utilizzare il prefisso Before o After negli eventi'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66e3d513188093a29aa9f7bb1c9f83b9c70e54d3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915313"
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713: Non utilizzare il prefisso Before o After negli eventi
|||
|-|-|
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|
|CheckId|CA1713|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Il nome di un evento inizia con "Before" o "After".

## <a name="rule-description"></a>Descrizione della regola
 I nomi degli eventi deve descrivere l'azione che genera l'evento. Per denominare eventi correlati generati in una sequenza specifica, utilizzare i tempi verbali presente o passato per indicare la posizione relativa nella sequenza di azioni. Ad esempio, quando una coppia di eventi di denominazione che viene generato alla chiusura di una risorsa, si potrebbe denominarla "Closing" e "Closed" anziché "BeforeClose" e "AfterClose".

 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la confidenza di clienti che la libreria è stata sviluppata da un utente che ha esperienza nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rimuovere il prefisso dal nome dell'evento, quindi provare a modificare il nome da utilizzare il presente o passato di un verbo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.