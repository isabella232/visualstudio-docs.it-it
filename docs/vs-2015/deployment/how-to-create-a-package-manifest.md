---
title: 'Procedura: creare un manifesto di pacchetto | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: 6abbbb351d04251b4ef1c209f35652a91b11d8c5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530414"
---
# <a name="how-to-create-a-package-manifest"></a>Procedura: creare un manifesto di pacchetto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: creare un manifesto del pacchetto](https://docs.microsoft.com/visualstudio/deployment/how-to-create-a-package-manifest).  
  
Per distribuire i prerequisiti per l'applicazione, è possibile usare un pacchetto di programma di avvio automatico. Un pacchetto bootstrapper contiene un file manifesto singolo prodotto ma un manifesto di pacchetto per ogni impostazione locale. Le funzionalità condivise tra le versioni localizzate che devono essere inserite il manifesto del prodotto.  
  
 Per altre informazioni sui manifesti di pacchetto, vedere [procedura: creare un manifesto del prodotto](../deployment/how-to-create-a-product-manifest.md).  
  
## <a name="creating-the-package-manifest"></a>Creazione del manifesto del pacchetto  
  
#### <a name="to-create-the-package-manifest"></a>Per creare il manifesto del pacchetto  
  
1.  Creare una directory per il pacchetto di programma di avvio automatico. Questo esempio Usa c:\package.  
  
2.  Creare una sottodirectory con il nome delle impostazioni locali, ad esempio en per inglese.  
  
3.  In Visual Studio, creare un file XML denominato `package.xml`e salvarlo nella cartella c:\package\en.  
  
4.  Aggiungere codice XML per elencare il nome del pacchetto, le impostazioni cultura per questo manifesto del pacchetto di aggiornamento e il contratto di licenza facoltativo. Il codice XML seguente usa le variabili `DisplayName` e `Culture`, che sono definiti in un elemento successivo.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  Aggiungere codice XML per elencare tutti i file che si trovano nella directory specifiche delle impostazioni locali. Il codice XML seguente viene utilizzato un file denominato EULA. txt è applicabile per il **en** delle impostazioni locali.  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  Aggiungere codice XML per definire le stringhe localizzabili per il pacchetto di programma di avvio automatico. Il codice XML seguente aggiunge le stringhe di errore per le impostazioni locali en.  
  
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
  
7.  Copiare la cartella c:\package. nella directory di avvio automatico di Visual Studio. Per Visual Studio 2010, si tratta della directory di Sdks\windows\v7.0A\Bootstrapper\Packages. \Programmi\Microsoft.  
  
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



