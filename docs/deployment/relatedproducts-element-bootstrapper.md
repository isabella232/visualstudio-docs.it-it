---
title: '&lt;&gt;Elemento RelatedProducts (programma di avvio automatico) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42756b21e631ec14e9c590833f6f0e95a317cc22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "66747464"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;&gt;Elemento RelatedProducts (programma di avvio automatico)
L' `RelatedProducts` elemento definisce altri prodotti che dipendono da o sono inclusi nel prodotto corrente.

## <a name="syntax"></a>Sintassi

```xml
<RelatedProducts>
    <DependsOnProduct
        Code
    />
    <EitherProducts>
        <DependsOnProduct
            Code
        />
    </EitherProducts>
    <IncludesProduct
        Code
    />
</RelatedProducts>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L' `RelatedProducts` elemento è un elemento figlio dell' `Product` elemento. Non ha attributi.

## <a name="dependsonproduct"></a>DependsOnProduct
 L' `DependsOnProduct` elemento indica che il prodotto corrente dipende dal prodotto denominato e che il prodotto denominato deve essere installato prima di quello corrente. È un elemento figlio dell' `RelatedProducts` elemento. Un `RelatedProducts` elemento può contenere uno o più `DependsOnProduct` elementi.

 `DependsOnProduct` ha l'attributo seguente.

|Attributo|Descrizione|
|---------------|-----------------|
|`Code`|Nome del codice del prodotto incluso, come specificato dall' `ProductCode` attributo dell' `Product` elemento. Per ulteriori informazioni, vedere [ \<Product> elemento](../deployment/product-element-bootstrapper.md).|

## <a name="eitherproducts"></a>EitherProducts
 L' `EitherProducts` elemento definisce zero o più `DependsOnProduct` elementi e non ha attributi. Almeno un `DependsOnProduct` in questo set deve essere installato prima del prodotto corrente. Un `RelatedProducts` elemento può contenere zero o più `EitherProducts` elementi.

## <a name="includesproduct"></a>IncludesProduct
 L' `IncludesProduct` elemento indica che un prodotto è incluso nell'installazione corrente e non richiede un'installazione separata. È un elemento figlio dell' `RelatedProducts` elemento. Un `RelatedProducts` elemento può contenere uno o più `IncludesProduct` elementi.

 `IncludesProduct` ha l'attributo seguente.

|Attributo|Descrizione|
|---------------|-----------------|
|`Code`|Nome del codice del prodotto incluso, come specificato dall' `ProductCode` attributo dell' `Product` elemento. Per ulteriori informazioni, vedere [ \<Product> elemento](../deployment/product-element-bootstrapper.md).|

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene specificato che Microsoft Installer viene installato con il .NET Framework e pertanto non sarà necessaria un'installazione separata.

```xml
<RelatedProducts>
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />
</RelatedProducts>
```

## <a name="see-also"></a>Vedere anche
- [\<Product> elemento](../deployment/product-element-bootstrapper.md)