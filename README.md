			getgenv().autofarm19 = true--true to make it on,false to make it stop
	
			while autofarm19 do
				-- Script generated by SimpleSpy - credits to exx#9394
	
				local args = {
					[1] = "GetQuest",
					[2] = 19
				}
	
				game:GetService("ReplicatedStorage").RemoteEvent:FireServer(unpack(args))
	
				wait(5)
				game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = Selected
			end
	
	
			coroutine.wrap(function()
				while wait() do
					if getgenv().autofarm19 == true then
						pcall(function()
							for i,v in pairs(game:GetService("Workspace").Spawns.Psykos:GetChildren()) do --enemy location
								if v:IsA("Model") and v.Name == "Bahiri" then --remove this if you want farm all mobs 
									if v.Humanoid.Health > 0 and game.Players.LocalPlayer.Character.Humanoid.Health > 0 then
										repeat
											wait()
											game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0,0,0)
										until v.Humanoid.Health <= 0 or getgenv().autofarm19 == false
									end
								end
							end
						end)
					end
				end
			end)()
	
	
			--no clip on when you start to farm,you can remove it if you dont want use noclip
			game:GetService("RunService").RenderStepped:Connect(function() 
				if autofarm19 == true then
					game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
				end
			end)
