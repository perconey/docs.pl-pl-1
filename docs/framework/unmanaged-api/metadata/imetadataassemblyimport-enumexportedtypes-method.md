---
title: "IMetaDataAssemblyImport::EnumExportedTypes — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.EnumExportedTypes
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 76c73cc3d13089b4a38a47d523d8baa77f6eed12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="e0a89-102">IMetaDataAssemblyImport::EnumExportedTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="e0a89-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="e0a89-103">Wylicza typy wyeksportowanego w manifeście zestawu w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="e0a89-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0a89-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0a89-104">Syntax</span></span>  
  
```  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,   
    [out] mdExportedType   rExportedTypes[],   
    [in]  ULONG            cMax,   
    [out] ULONG            *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e0a89-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0a89-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e0a89-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="e0a89-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e0a89-107">Musi to być wartość null wartość przy `EnumExportedTypes` metoda jest wywoływana po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="e0a89-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="e0a89-108">[out] Wyliczanie `mdExportedType` tokenów metadanych.</span><span class="sxs-lookup"><span data-stu-id="e0a89-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e0a89-109">[in] Maksymalna liczba `mdExportedType` tokenów, które można umieścić w `rExportedTypes` tablicy.</span><span class="sxs-lookup"><span data-stu-id="e0a89-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e0a89-110">[out] Liczba `mdExportedType` tokeny faktycznie umieszczone w `rExportedTypes`.</span><span class="sxs-lookup"><span data-stu-id="e0a89-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0a89-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e0a89-111">Return Value</span></span>  
  
|<span data-ttu-id="e0a89-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e0a89-112">HRESULT</span></span>|<span data-ttu-id="e0a89-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e0a89-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e0a89-114">`EnumExportedTypes`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e0a89-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e0a89-115">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="e0a89-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="e0a89-116">W takim przypadku `pcTokens` jest ustawiony na zero.</span><span class="sxs-lookup"><span data-stu-id="e0a89-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e0a89-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e0a89-117">Requirements</span></span>  
 <span data-ttu-id="e0a89-118">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0a89-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0a89-119">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e0a89-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e0a89-120">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e0a89-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e0a89-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0a89-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0a89-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0a89-122">See Also</span></span>  
 [<span data-ttu-id="e0a89-123">IMetaDataAssemblyImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="e0a89-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)