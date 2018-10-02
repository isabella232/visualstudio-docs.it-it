---
title: ': Eventi CA1713 non prefisso before o after | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 46ed0ad62d145b7c60c9f20e1a3770016098a236
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589183"
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713: Non utilizzare il prefisso Before o After negli eventi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1713: gli eventi non devono avere prefisso before o after](https://docs.microsoft.com/visualstudio/code-quality/ca1713-events-should-not-have-before-or-after-prefix).

|||
|-|-|
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|
|CheckId|CA1713|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Il nome di un evento inizia con 'Before' o 'After'.

## <a name="rule-description"></a>Descrizione della regola
 I nomi degli eventi deve descrivere l'azione che genera l'evento. Per denominare eventi correlati generati in una sequenza specifica, utilizzare i tempi verbali presente o passato per indicare la posizione relativa nella sequenza di azioni. Ad esempio, quando una coppia di eventi di denominazione che viene generato alla chiusura di una risorsa, si potrebbe denominarla "Closing" e "Closed", invece di 'BeforeClose' e 'AfterClose'.

 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente con competenze nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rimuovere il prefisso dal nome dell'evento e provare a modificare il nome da utilizzare il presente o passato di un verbo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.



