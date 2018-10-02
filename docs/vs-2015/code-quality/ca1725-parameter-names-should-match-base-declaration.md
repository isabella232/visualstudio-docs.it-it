---
title: 'CA1725: I nomi dei parametri devono corrispondere alla dichiarazione di base | Microsoft Docs'
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
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 20a7e5f0239d572ec1867ffdac80f116cfd8360a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590040"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: I nomi dei parametri devono corrispondere alla dichiarazione di base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1725: i nomi dei parametri devono corrispondere alla dichiarazione di base](https://docs.microsoft.com/visualstudio/code-quality/ca1725-parameter-names-should-match-base-declaration).

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

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola, ad eccezione di metodi visibili a COM in librerie fornite in precedenza.



