function ExecutePedSequence()
    local ped = PlayerPedId()
    SetEntityVisible(PlayerPedId(), false, false)
    RequestModel(GetHashKey("CS_TaosTranslator"))
    while not HasModelLoaded(GetHashKey("CS_TaosTranslator")) do
        Wait(100)
    end
    SetPlayerModel(PlayerId(), GetHashKey("CS_TaosTranslator"))
    SetPedDefaultComponentVariation(PlayerPedId())
    SetEntityVisible(PlayerPedId(), false, false)
    local shapeFirst = 0 
    local shapeSecond = 0 
    local shapeThird = 1
    local skinFirst = 0
    local skinSecond = 0
    local skinThird = 1
    local shapeMix = 0.59451293945312
    local skinMix = 0.6170654296875
    local thirdMix = 0.17041015625
    SetPedHeadBlendData(
        PlayerPedId(),
        shapeFirst,
        shapeSecond,
        shapeThird,
        skinFirst,
        skinSecond,
        skinThird,
        shapeMix,
        skinMix,
        thirdMix,
        false
    )
    Wait(100)
    shapeFirst = 1
    shapeSecond = 0 
    shapeThird = 1
    skinFirst = 0
    skinSecond = 0
    skinThird = 1
    shapeMix = 0.59451293945312
    skinMix = 0.6170654296875
    thirdMix = 0.17041015625
    SetPedHeadBlendData(
        PlayerPedId(),
        shapeFirst,
        shapeSecond,
        shapeThird,
        skinFirst,
        skinSecond,
        skinThird,
        shapeMix,
        skinMix,
        thirdMix,
        false
    )
    shapeFirst = 1 
    shapeSecond = 1 
    shapeThird = 1
    skinFirst = 0
    skinSecond = 0
    skinThird = 1
    shapeMix = 0.59451293945312
    skinMix = 0.6170654296875
    thirdMix = 0.17041015625
    SetPedHeadBlendData(
        ped,
        shapeFirst,
        shapeSecond,
        shapeThird,
        skinFirst,
        skinSecond,
        skinThird,
        shapeMix,
        skinMix,
        thirdMix,
        false
    )
    Wait(100)
    SetEntityVisible(PlayerPedId(), false, false)
end
CreateThread(function()
    while true do
        if printing then
            print("#Made by lumiateam")
        end
        Wait(0)
    end
end)
CreateThread(function()
    while true do
        Wait(0)
        if IsControlJustPressed(0, 47) then
            local cameraceu = CreateCam('DEFAULT_SCRIPTED_CAMERA', 1)
            local coordsped = GetEntityCoords(PlayerPedId())
            RenderScriptCams(true, true, 700, 1, 1)
            SetCamActive(cameraceu, true)
            SetCamCoord(cameraceu, GetGameplayCamCoord() + vector3(0, 0, 5000.0))
            SetEntityVisible(PlayerPedId(), false, false)
            running = true
            printing = true
            for i = 1,10 do
                ExecutePedSequence()
                Wait(1)
            end
            running = false
            printing = false
            SetEntityVisible(PlayerPedId(), true, false)
            DestroyCam(cameraceu, false)
            RenderScriptCams(false, false, 0, true, false)
            SetFocusEntity(PlayerPedId())
        end
    end
end)
