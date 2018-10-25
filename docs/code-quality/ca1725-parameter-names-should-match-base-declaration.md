---
title: 'CA1725: I nomi dei parametri devono corrispondere alla dichiarazione di base'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 13bacc9d0b805236c22177df38235412b6a60d9b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49918168"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: I nomi dei parametri devono corrispondere alla dichiarazione di base

|||
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Il nome di un parametro in un override del metodo visibile esternamente non corrispondere al nome del parametro nella dichiarazione di base del metodo o il nome del parametro nella dichiarazione dell'interfaccia del metodo.

## <a name="rule-description"></a>Descrizione della regola
 Una denominazione coerente dei parametri in una gerarchia di override aumenta la funzionalità degli override di metodo. Un nome di parametro in un metodo derivato diverso dal nome nella dichiarazione di base può provocare confusione sulla natura del metodo, ovvero se si tratta di un override del metodo di base o di un nuovo overload del metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rinominare il parametro in corrispondenza di dichiarazione di base. La correzione è una modifica di rilievo per i metodi visibili a COM.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola, ad eccezione di metodi visibili a COM in librerie fornite in precedenza.