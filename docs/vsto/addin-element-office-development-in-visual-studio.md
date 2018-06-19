---
title: '&lt;componente aggiuntivo&gt; elemento (sviluppo per Office in Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <addIn> element
- addin element
- <addin> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1d2ab0264452630892d492946462fbf9ad1639d0
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262382"
---
# <a name="ltaddingt-element-office-development-in-visual-studio"></a>&lt;componente aggiuntivo&gt; elemento (sviluppo per Office in Visual Studio)
  Il **addin** elemento del `vstav3` dello spazio dei nomi contiene informazioni che sono specifiche di componenti aggiuntivi VSTO per Microsoft Office e le personalizzazioni a livello di documento sviluppate con Visual Studio.  

## <a name="syntax"></a>Sintassi  

```xml
<addIn>  
  <entryPointsCollection>  
    <entryPoints>  
      <entryPoint>  
      </entryPoint>  
    </entryPoints>  
  </entryPointsCollection>  
  <update></update>  
  <postActions>  
    <postAction>  
      <postActionData>  
      </postActionData>  
    <postAction>  
  </postActions>  
  <application>  
    <customization>  
    </customization>  
  </application  
</addIn>  
```  

## <a name="elements-and-attributes"></a>Elementi e attributi  
 Il **addin** elemento del `vstav3` dello spazio dei nomi contiene informazioni sulla soluzione Office e l'applicazione di Microsoft Office. Questo elemento deve essere presente nello spazio dei nomi seguente: `vstav3=urn:schemas-microsoft-com:vsta.v3`. Anche gli elementi figlio devono trovarsi in questo spazio dei nomi.  

 L'elemento `addin` non ha attributi.  

 L'elemento `addin` ha gli elementi figlio seguenti.  

### <a name="entrypoints"></a>entryPoints  
 Obbligatorio. Il **entryPoints** elemento viene descritto [ &#60;entryPoints&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).  

### <a name="update"></a>aggiorna  
 Obbligatorio. Il **aggiornare** elemento viene descritto [ &#60;Aggiorna&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md).  

### <a name="postactions"></a>postActions  
 Facoltativo. Il **postActions** elemento viene descritto [ &#60;postActions&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md).  

### <a name="application"></a>applicazione  
 Obbligatorio. Il **applicazione** elemento viene descritto [ &#60;applicazioni&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md).  

## <a name="document-level-customization-example"></a>Esempio di personalizzazione a livello di documento  

### <a name="description"></a>Descrizione  
 L'esempio di codice seguente illustra la **addin** elemento in una soluzione Office a livello di documento distribuita tramite [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  

### <a name="code"></a>Codice  

```xml
<vstav3:addIn   
  xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3">  
  <vstav3:entryPointsCollection>  
    <vstav3:entryPoints>  
      <vstav3:entryPoint   
        class="ContosoExcelWorkbook.ThisWorkbook">  
        <assemblyIdentity   
          name="ContosoExcelWorkbook"   
          version="1.0.0.0"   
          language="neutral"   
          processorArchitecture="msil" />  
      </vstav3:entryPoint>  
      <vstav3:entryPoint   
        class="ContosoExcelWorkbook.Sheet1">  
        <assemblyIdentity   
          name="ContosoExcelWorkbook"   
          version="1.0.0.0"   
          language="neutral"   
          processorArchitecture="msil" />  
      </vstav3:entryPoint>  
      <vstav3:entryPoint   
        class="ContosoExcelWorkbook.Sheet2">  
        <assemblyIdentity   
          name="ContosoExcelWorkbook"   
          version="1.0.0.0"   
          language="neutral"   
          processorArchitecture="msil" />  
      </vstav3:entryPoint>  
      <vstav3:entryPoint   
        class="ContosoExcelWorkbook.Sheet3">  
        <assemblyIdentity   
          name="ContosoExcelWorkbook"   
          version="1.0.0.0"   
          language="neutral"   
          processorArchitecture="msil" />  
      </vstav3:entryPoint>  
    </vstav3:entryPoints>  
  </vstav3:entryPointsCollection>  
  <vstav3:update   
    enabled="true">  
    <vstav3:expiration   
      maximumAge="7"   
      unit="days" />  
  </vstav3:update>  
  <vstav3:application>  
    <vstov4:customizations   
      xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
      <vstov4:customization>  
        <vstov4:document   
          solutionId="73e" />  
      </vstov4:customization>  
    </vstov4:customizations>  
  </vstav3:application>  
</vstav3:addIn>  
```  

## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO  

### <a name="description"></a>Descrizione  
 L'esempio di codice seguente illustra la **addin** elemento in una soluzione Office a livello di applicazione che viene distribuito usando [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  

### <a name="code"></a>Codice  

```xml
<vstav3:addIn   
  xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3">  
  <vstav3:entryPointsCollection>  
    <vstav3:entryPoints>  
      <vstav3:entryPoint   
        class="ContosoOutlookAddIn.ThisAddIn">  
        <assemblyIdentity   
          name="ContosoOutlookAddIn"   
          version="1.0.0.0"   
          language="neutral"   
          processorArchitecture="msil" />  
      </vstav3:entryPoint>  
    </vstav3:entryPoints>  
  </vstav3:entryPointsCollection>  
  <vstav3:update   
    enabled="true">  
    <vstav3:expiration   
      maximumAge="7"   
      unit="days" />  
  </vstav3:update>  
  <vstav3:application>  
    <vstov4:customizations   
      xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
      <vstov4:customization>  
        <vstov4:appAddIn   
          application="Outlook"   
          loadBehavior="3"   
          keyName="ContosoOutlookAddIn">  
          <vstov4:friendlyName>  
            ContosoOutlookAddIn  
          </vstov4:friendlyName>  
          <vstov4:description>  
            ContosoOutlookAddIn - Outlook VSTO Add-in   
            created with Visual Studio Tools for Office  
          </vstov4:description>  
          <vstov4:formRegions>  
            <vstov4:formRegion  
                name="OutlookAddIn1.FormRegion1">  
              <vstov4:messageClass name="IPM.Note" />  
              <vstov4:messageClass name="IPM.Contact" />  
              <vstov4:messageClass name="IPM.Appointment" />  
            </vstov4:formRegion>  
          </vstov4:formRegions>  
        </vstov4:appAddIn>  
      </vstov4:customization>  
    </vstov4:customizations>  
  </vstav3:application>  
</vstav3:addIn>  
```  

## <a name="see-also"></a>Vedere anche  
 [Manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifesto dell'applicazione ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
