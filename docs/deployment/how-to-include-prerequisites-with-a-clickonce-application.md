---
title: "Procedura: includere i prerequisiti con un'applicazione ClickOnce | Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3f961229e60cb291efdd7630f9df10e162c2f17b
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153842"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Procedura: includere i prerequisiti con un'applicazione ClickOnce
Prima di poter distribuire i prerequisiti relativi al software con un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], è necessario scaricare i pacchetti di installazione per quei prerequisiti nel computer di sviluppo. Quando si pubblica un'applicazione e scegliere **Scarica prerequisiti dallo stesso percorso dell'applicazione**, si verificherà un errore se i pacchetti di installazione non sono presenti le **pacchetti** cartella.  
  
> [!NOTE]
>  Per aggiungere un pacchetto di installazione di .NET Framework, vedere [Guida alla distribuzione di .NET Framework per sviluppatori](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).  
  
##  <a name="Package"></a> Per aggiungere un pacchetto di installazione tramite package. Xml  
  
1.  In Esplora File, aprire il **pacchetti** cartella.  
  
     Per impostazione predefinita, il percorso corrisponde *C:\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages* in un sistema a 32 bit e *C:\Program Files (x86) \Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages* in un sistema a 64 bit.  
  
2.  Aprire la cartella per i prerequisiti che si desidera aggiungere e quindi aprire la cartella del linguaggio per la versione installata di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (ad esempio **en** per la lingua inglese).  
  
3.  Nel blocco note, aprire il *package* file.  
  
4.  Individuare il **Name** elemento contenente **http://go.microsoft.com/fwlink**e copiare l'URL. Includere il **LinkID** parte.  
  
    > [!NOTE]
    >  Se nessun **Name** elemento contiene **http://go.microsoft.com/fwlink**, aprire il **Product** file nella cartella radice del prerequisito e individuare il **fwlink** stringa.  
  
    > [!IMPORTANT]
    >  Alcuni prerequisiti hanno più pacchetti di installazione (ad esempio, per sistemi a 32 bit o a 64 bit). Se più **Name** elementi contengono **fwlink**, è necessario ripetere i passaggi rimanenti per ognuno di essi.  
  
5.  Incollare l'URL nella barra degli indirizzi del browser e quindi, quando viene chiesto di eseguire o salvare, scegliere **salvare**.  
  
     Questo passaggio consente di scaricare il file del programma di installazione nel computer.  
  
6.  Copiare il file nella cartella radice del prerequisito.  
  
     Ad esempio, per il prerequisito di Windows Installer 4.5, copiare il file per il *\Packages\WindowsInstaller4_5* cartella.  
  
     È ora possibile distribuire il pacchetto di installazione con la propria applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: installare i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)