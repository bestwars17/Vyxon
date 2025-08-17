ServerTab:AddLabel("Fast Rebirths")
ServerTab:AddSwitch("Fast Rebirths | Required New Packs |", function(state)
    getgenv().fastRebirths = state
    task.spawn(function()
        while getgenv().fastRebirths and LocalPlayer.Character do
            ReplicatedStorage.rEvents.rebirthRemote:InvokeServer("rebirthRequest")
            task.wait(0.1)
        end
    end)
end)
