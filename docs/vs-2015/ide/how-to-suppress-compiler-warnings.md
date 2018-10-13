---
title: 'Procedura: Non visualizzare avvisi del compilatore | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 738934450536d6ae51e67223c440e607ac6b6839
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49286091"
---
# <a name="how-to-suppress-compiler-warnings"></a>Procedura: non visualizzare avvisi del compilatore
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile ripulire un log di compilazione specificando uno o più tipi di avvisi del compilatore che non devono essere contenuti nel log. È ad esempio possibile usare questa tecnica per rivedere alcune ma non tutte le informazioni generate automaticamente quando il livello di dettaglio del log di compilazione viene impostato su Normale, Dettagliato o Diagnostico. Per altre informazioni sul livello di dettaglio, vedere [How to: View, Save, and Configure Build Log Files](../ide/how-to-view-save-and-configure-build-log-files.md) (Procedura: Visualizzare, salvare e configurare file di log di compilazione)  
  
### <a name="to-suppress-specific-warnings-for-visual-c-or-f"></a>Per non visualizzare avvisi specifici per Visual C# o F#  
  
1.  In **Esplora soluzioni** scegliere il progetto in cui non devono essere visualizzati gli avvisi.  
  
2.  Sulla barra dei menu, scegliere **Visualizza**, **Pagine delle proprietà**.  
  
3.  Scegliere la scheda **Compila**.  
  
4.  Nella casella **Non visualizzare avvisi** specificare i codici di errore degli avvisi che non devono essere visualizzati, separati da punti e virgola, e ricompilare la soluzione.  
  
### <a name="to-suppress-specific-warnings-for-visual-c"></a>Per non visualizzare avvisi specifici per Visual C++  
  
1.  In **Esplora soluzioni** scegliere il progetto o il file di origine in cui non devono essere visualizzati gli avvisi.  
  
2.  Sulla barra dei menu, scegliere **Visualizza**, **Pagine delle proprietà**.  
  
3.  Scegliere la categoria **Proprietà di configurazione**, selezionare la categoria **C/C++** e scegliere la pagina **Avanzate**.  
  
4.  Effettuare uno dei passaggi indicati di seguito.  
  
    -   Nella casella **Disabilita avvisi specifici** specificare i codici di errore degli avvisi che non devono essere visualizzati, separati da punto e virgola.  
  
    -   Nella casella **Disabilita avvisi specifici** scegliere **Modifica** per visualizzare altre opzioni.  
  
5.  Fare clic sul pulsante **OK** e ricompilare la soluzione.  
  
## <a name="suppressing-warnings-for-visual-basic"></a>Avvisi non visualizzati per Visual Basic  
 È possibile nascondere gli avvisi del compilatore specifici per Visual Basic modificando il file con estensione vbproj per il progetto. È anche possibile usare la [pagina Compilazione di Creazione progetti (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md) per scegliere di non visualizzare gli di avvisi in base alla categoria. Per altre informazioni, vedere [Configuring Warnings in Visual Basic](../ide/configuring-warnings-in-visual-basic.md) (Configurazione degli avvisi in Visual Basic).  
  
#### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Per non visualizzare avvisi specifici per Visual Basic  
  
1.  In **Esplora soluzioni** scegliere il progetto in cui non devono essere visualizzati gli avvisi.  
  
2.  Sulla barra dei menu scegliere **Progetto**, **Scarica progetto**.  
  
3.  In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto e scegliere **Modifica**_nomeprogetto_**.vbproj**.  
  
     Il file di progetto si aprirà nell'editor del codice.  
  
4.  Individuare l'elemento `<NoWarn></NoWarn>` nella configurazione della build che si sta usando per la compilazione.  
  
     Nell'esempio seguente viene indicato l'elemento `<NoWarn></NoWarn>` in grassetto per la configurazione della build di debug su una piattaforma x86:  
  
    ```  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
        <PlatformTarget>x86</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <ErrorReport>prompt</ErrorReport>  
        <NoWarn></NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
5.  Aggiungere uno o più numeri di avviso come valore dell'elemento `<NoWarn>`. Se si specificano più numeri di avviso, è necessario separarli con una virgola, come illustrato nell'esempio seguente.  
  
    ```  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
        <PlatformTarget>x86</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <ErrorReport>prompt</ErrorReport>  
        <NoWarn>40059,42024</NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
6.  Salvare le modifiche apportate al file con estensione vbproj.  
  
7.  Sulla barra dei menu scegliere **Progetto**, **Ricarica progetto**.  
  
8.  Sulla barra dei menu scegliere **Compila**, **Ricompila soluzione**.  
  
     Nella finestra **Output** gli avvisi specificati non saranno più visualizzati.  
  
 Per altre informazioni, vedere [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).  
  
## <a name="see-also"></a>Vedere anche  
 [Walkthrough: Building an Application](../ide/walkthrough-building-an-application.md)  (Procedura dettagliata: compilazione di un'applicazione)  
 [How to: View, Save, and Configure Build Log Files](../ide/how-to-view-save-and-configure-build-log-files.md)  (Procedura: Visualizzare, salvare e configurare file di log di compilazione)  
 [Compiling and Building](../ide/compiling-and-building-in-visual-studio.md) (Compilazione e creazione)



