---
title: 'Procedura: Creare un manifesto di pacchetto | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c711c50ab484cc88b1d6aff5c8e3018cead69953
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60046015"
---
# <a name="how-to-create-a-package-manifest"></a>Procedura: Creare un manifesto di pacchetto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per distribuire i prerequisiti per l'applicazione, è possibile usare un pacchetto di programma di avvio automatico. Un pacchetto bootstrapper contiene un file manifesto singolo prodotto ma un manifesto di pacchetto per ogni impostazione locale. Le funzionalità condivise tra le versioni localizzate che devono essere inserite il manifesto del prodotto.  
  
 Per altre informazioni sui manifesti di pacchetto, vedere [come: Creare un manifesto del prodotto](../deployment/how-to-create-a-product-manifest.md).  
  
## <a name="creating-the-package-manifest"></a>Creazione del manifesto del pacchetto  
  
#### <a name="to-create-the-package-manifest"></a>Per creare il manifesto del pacchetto  
  
1. Creare una directory per il pacchetto di programma di avvio automatico. Questo esempio Usa c:\package.  
  
2. Creare una sottodirectory con il nome delle impostazioni locali, ad esempio en per inglese.  
  
3. In Visual Studio, creare un file XML denominato `package.xml`e salvarlo nella cartella c:\package\en.  
  
4. Aggiungere codice XML per elencare il nome del pacchetto, le impostazioni cultura per questo manifesto del pacchetto di aggiornamento e il contratto di licenza facoltativo. Il codice XML seguente usa le variabili `DisplayName` e `Culture`, che sono definiti in un elemento successivo.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5. Aggiungere codice XML per elencare tutti i file che si trovano nella directory specifiche delle impostazioni locali. Il codice XML seguente viene utilizzato un file denominato EULA. txt è applicabile per il **en** delle impostazioni locali.  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6. Aggiungere codice XML per definire le stringhe localizzabili per il pacchetto di programma di avvio automatico. Il codice XML seguente aggiunge le stringhe di errore per le impostazioni locali en.  
  
    ```  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7. Copiare la cartella c:\package. nella directory di avvio automatico di Visual Studio. Per Visual Studio 2010, si tratta della directory di Sdks\windows\v7.0A\Bootstrapper\Packages. \Programmi\Microsoft.  
  
## <a name="example"></a>Esempio  
 Il manifesto del pacchetto contiene informazioni specifiche delle impostazioni locali, ad esempio i messaggi di errore, condizioni di licenza software e i language pack.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Package  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  Name="DisplayName"  
  Culture="Culture"  
  LicenseAgreement="eula.txt">  
  
  <PackageFiles>  
    <PackageFile Name="eula.txt"/>  
  </PackageFiles>  
  
  <Strings>  
    <String Name="DisplayName">Custom Bootstrapper Package</String>  
    <String Name="Culture">en</String>  
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>  
    <String Name="GeneralFailure">A general error has occurred while   
installing this package.</String>  
  </Strings>  
</Package>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti dello schema di prodotti e package](../deployment/product-and-package-schema-reference.md)
