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
ms.openlocfilehash: d3564f3713dd24488e71703e902ae63f09b6aa74
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914341"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: I nomi dei parametri devono corrispondere alla dichiarazione di base
|||
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Il nome di un parametro in un override del metodo visibile esternamente non corrispondere al nome del parametro nella dichiarazione di base del metodo o il nome del parametro nella dichiarazione del metodo di interfaccia.

## <a name="rule-description"></a>Descrizione della regola
 Una denominazione coerente dei parametri in una gerarchia di override aumenta la funzionalità degli override di metodo. Un nome di parametro in un metodo derivato diverso dal nome nella dichiarazione di base può provocare confusione sulla natura del metodo, ovvero se si tratta di un override del metodo di base o di un nuovo overload del metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rinominare il parametro in corrispondenza di dichiarazione di base. Per risolvere il problema è una modifica di rilievo per metodi visibili a COM.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola, ad eccezione di metodi visibili a COM in librerie fornite in precedenza.