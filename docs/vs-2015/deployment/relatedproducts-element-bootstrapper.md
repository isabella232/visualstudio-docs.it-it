---
title: '&lt;&gt;Elemento RelatedProducts (programma di avvio automatico) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 70afe724be5b782bc90e162fd65f83ad1b0d0d23
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202530"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;&gt;Elemento RelatedProducts (programma di avvio automatico)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L' `RelatedProducts` elemento definisce altri prodotti che dipendono da o sono inclusi nel prodotto corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
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
 Nell'esempio di codice seguente viene specificato che Microsoft Installer è installato con [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] e pertanto non sarà necessaria un'installazione separata.  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [\<Product> Elemento](../deployment/product-element-bootstrapper.md)
