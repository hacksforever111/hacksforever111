- 👋 Hi, I’m @hacksforever111
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
hacksforever111/hacksforever111 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
--[[ loadstring(game:HttpGet(('https://pastebin.com/raw/ibcp0DZc'),true))() ]]

local plr = game.Players.LocalPlayer;
repeat wait(); until plr.Character;
local char = plr.Character;
local zombie_storage = workspace:WaitForChild("Zombie Storage");
local mouse = plr:GetMouse();
local hide_zombie_names = false;

local menu_settings = {
	menu_status = "Undetectable",
	tick_sound = "rbxassetid://156286438",
	hover_sound = "rbxassetid://3199281218",
	menu_version = "1.0.0",
	menu_color = Color3.fromRGB(130,167,217),
	menu_highlight_color = Color3.fromRGB(200,200,200),
	menu_leave_color = Color3.fromRGB(240, 240, 240),
	menu_font = "Code",
	menu_color_close = "rbxassetid://3857981268",
	menu_settings_icon = "rbxassetid://3857990390",
	menu_in_settings = false
}

local menu_color_names = {
	"blue","red","green","purple","pink","orange","grey","black"
}

local menu_color_opts = {
	blue = Color3.fromRGB(130, 167, 217),
	red = Color3.fromRGB(226, 95, 97),
	green = Color3.fromRGB(130, 226, 182),
	purple = Color3.fromRGB(206, 60, 206),
	pink = Color3.fromRGB(255, 133, 229),
	orange = Color3.fromRGB(245, 176, 55),
	grey = Color3.fromRGB(171, 171, 171),
	black = Color3.fromRGB(0, 0, 0)
}

local super_speed_settings = {
	super_speed = false;
	speed = 80;
}

local super_jump_settings = {
	super_jump = false;
	height = 120;
}

local rgb_settings = {
	rgb = false	
}

local checkbox_settings = {
	tik = "✓",
	null = "",
	tik_c = Color3.fromRGB(39,134,34),
	null_c = Color3.fromRGB(0,0,0)
}

local promod_settings = {
	promod = false,
	default_fov = 70,
	promod_fov = 95	
}

local flyhack_settings = {
	flyhack = false;
	ctrl = {f = 0, b = 0, l = 0, r = 0},
	lastctrl = {f = 0, b = 0, l = 0, r = 0},
	flyhack_maxspeed = 45,
	flyhack_speed = 0
}

local esp_settings = {
	esp = false,
	esp_c = Color3.fromRGB(255,0,0),
	esp_p_c = Color3.fromRGB(0,255,0),
	faces = {"Front","Back","Bottom","Left","Right","Top"}
}

local menu_options = {
	"[chams]","[noclip]","[promod]","[super_speed]","[super_jump]","[fullbright]","[hide_names]"
}

local fullbright = false;

function superSpeed(bool)
	if bool then
		char['Humanoid'].WalkSpeed = 55;
	else
		char['Humanoid'].WalkSpeed = 16;
	end
end

function superJump(bool)
	if bool then
		char['Humanoid'].JumpPower = super_jump_settings.height;
	else
		char['Humanoid'].JumpPower = 50;
	end
end

function graphicsMode(bool)
	if bool then
		local bloom = Instance.new("BloomEffect");
		bloom.Enabled = true;
		bloom.Intensity = 0.55;
		bloom.Size = 30;
		bloom.Threshold = 0.95;
		bloom.Parent = game.Lighting;
		local colorcorrection = Instance.new("ColorCorrectionEffect");
		colorcorrection.Enabled = true;
		colorcorrection.Brightness = 0;
		colorcorrection.Contrast = 0;
		colorcorrection.Saturation = 1;
		colorcorrection.TintColor = Color3.fromRGB(255,255,255);
		colorcorrection.Parent = game.Lighting;
		local sunrays = Instance.new("SunRaysEffect");
		sunrays.Enabled = true;
		sunrays.Intensity = 0.4;
		sunrays.Spread = 1;
		sunrays.Parent = game.Lighting;
	else
		for i,v in pairs(game.Lighting:GetChildren()) do
			if v:IsA("BloomEffect") or v:IsA("ColorCorrectionEffect") or v:IsA("SunRaysEffect") then
				v:Destroy();
			end
		end
	end
end

function proMod(bool)
	if bool then
		workspace.Camera.FieldOfView = promod_settings.promod_fov;
	else
		workspace.Camera.FieldOfView = promod_settings.default_fov;
	end
end

function flyHack()
	local torso = char['HumanoidRootPart'];
	local bg = Instance.new("BodyGyro", torso) 
	bg.maxTorque = Vector3.new(9e9, 9e9, 9e9) 
	bg.cframe = torso.CFrame 
	local bv = Instance.new("BodyVelocity", torso) 
	bv.velocity = Vector3.new(0,0.1,0) 
	bv.maxForce = Vector3.new(9e9, 9e9, 9e9) 
	repeat wait()
	plr.Character.Humanoid.PlatformStand = true 
	if flyhack_settings.ctrl.l + flyhack_settings.ctrl.r ~= 0 or flyhack_settings.ctrl.f + flyhack_settings.ctrl.b ~= 0 then 
		flyhack_settings.flyhack_speed = flyhack_settings.flyhack_speed+.5+(flyhack_settings.flyhack_speed/flyhack_settings.flyhack_maxspeed) 
		if flyhack_settings.flyhack_speed > flyhack_settings.flyhack_maxspeed then 
			flyhack_settings.flyhack_speed = flyhack_settings.flyhack_maxspeed 
		end 
		elseif not (flyhack_settings.ctrl.l + flyhack_settings.ctrl.r ~= 0 or flyhack_settings.ctrl.f + flyhack_settings.ctrl.b ~= 0) and flyhack_settings.flyhack_speed ~= 0 then 
			flyhack_settings.flyhack_speed = flyhack_settings.flyhack_speed-1 
			if flyhack_settings.flyhack_speed < 0 then 
				flyhack_settings.flyhack_speed = 0 
			end 
		end 
		if (flyhack_settings.ctrl.l + flyhack_settings.ctrl.r) ~= 0 or (flyhack_settings.ctrl.f + flyhack_settings.ctrl.b) ~= 0 then 
			bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (flyhack_settings.ctrl.f+flyhack_settings.ctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(flyhack_settings.ctrl.l+flyhack_settings.ctrl.r,(flyhack_settings.ctrl.f+flyhack_settings.ctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*flyhack_settings.flyhack_speed 
			flyhack_settings.lastctrl = {f = flyhack_settings.ctrl.f, b = flyhack_settings.ctrl.b, l = flyhack_settings.ctrl.l, r = flyhack_settings.ctrl.r} 
		elseif (flyhack_settings.ctrl.l + flyhack_settings.ctrl.r) == 0 and (flyhack_settings.ctrl.f + flyhack_settings.ctrl.b) == 0 and flyhack_settings.flyhack_speed ~= 0 then 
			bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (flyhack_settings.lastctrl.f+flyhack_settings.lastctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(flyhack_settings.lastctrl.l+flyhack_settings.lastctrl.r,(flyhack_settings.lastctrl.f+flyhack_settings.lastctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*flyhack_settings.flyhack_speed 
		else 
			bv.velocity = Vector3.new(0,0.1,0) 
		end 
		bg.cframe = game.Workspace.CurrentCamera.CoordinateFrame * CFrame.Angles(-math.rad((flyhack_settings.ctrl.f+flyhack_settings.ctrl.b)*50*flyhack_settings.flyhack_speed/flyhack_settings.flyhack_maxspeed),0,0) 
	until not flyhack_settings.flyhack 
	flyhack_settings.ctrl = {f = 0, b = 0, l = 0, r = 0} 
	flyhack_settings.lastctrl = {f = 0, b = 0, l = 0, r = 0} 
	flyhack_settings.flyhack_speed = 0 
	bg:Destroy() 
	bv:Destroy() 
	plr.Character.Humanoid.PlatformStand = false 
end

mouse.KeyDown:connect(function(key) 
	if flyhack_settings.flyhack then
		if key:lower() == "w" then 
			flyhack_settings.ctrl.f = 1 
		elseif key:lower() == "s" then 
			flyhack_settings.ctrl.b = -1 
		elseif key:lower() == "a" then 
			flyhack_settings.ctrl.l = -1 
		elseif key:lower() == "d" then 
			flyhack_settings.ctrl.r = 1 
		end
	end
end) 

mouse.KeyUp:connect(function(key)
	if flyhack_settings.flyhack then
		if key:lower() == "w" then 
			flyhack_settings.ctrl.f = 0 
		elseif key:lower() == "s" then 
			flyhack_settings.ctrl.b = 0 
		elseif key:lower() == "a" then 
			flyhack_settings.ctrl.l = 0 
		elseif key:lower() == "d" then 
			flyhack_settings.ctrl.r = 0 
		end 
	end
end)

function removeZombieNames(bool)
	if bool then
		for i,v in pairs(zombie_storage:GetChildren()) do
			local hum = v:FindFirstChildOfClass("Humanoid");
			hum.DisplayDistanceType = "None";
		end
	else
		for i,v in pairs(zombie_storage:GetChildren()) do
			local hum = v:FindFirstChildOfClass("Humanoid");
			hum.DisplayDistanceType = "Viewer";
		end
	end
end

function createDistanceLines(part1,part2,player)
	local beam = Instance.new("Beam");
	local at1 = Instance.new("Attachment");
	local at2 = Instance.new("Attachment");
	if player then
		beam.Color = ColorSequence.new({
		ColorSequenceKeypoint.new(0, Color3.fromRGB(0,255,0)),
		ColorSequenceKeypoint.new(1, Color3.fromRGB(0,255,0))
		}
	)
	else
		beam.Color = ColorSequence.new({
		ColorSequenceKeypoint.new(0, Color3.fromRGB(255,0,0)),
		ColorSequenceKeypoint.new(1, Color3.fromRGB(255,0,0))
		}
	)
	end
	at1.Parent = part1;
	at2.Parent = part2;
	beam.Segments = 1;
	beam.Width0 = 0.1;
	beam.Width1 = 0.1;
	beam.Parent = part1;
	
	beam.Attachment0 = at1;
	beam.Attachment1 = at2;
end

function createFaces(obj,player)
	for i=0,5 do
		local surface = Instance.new("SurfaceGui",obj);
		surface.Face = Enum.NormalId[esp_settings.faces[i+1]];
		surface.AlwaysOnTop = true
		local frame = Instance.new("Frame",surface);
		frame.Size = UDim2.new(1,0,1,0);
		frame.BorderSizePixel = 0 ;                                             
		frame.BackgroundTransparency = 0.5;
		if player then
			frame.BackgroundColor3 = esp_settings.esp_p_c;  
		else
			frame.BackgroundColor3 = esp_settings.esp_c;  
		end                         
    end
end

function destroyFaces(z)
	for i,v in pairs(z:GetChildren()) do
		if v:FindFirstChildOfClass("SurfaceGui") then
			for i,j in pairs(v:GetChildren()) do
				if j:IsA("SurfaceGui") then
					j:Destroy();
				end
				if j.Name == "Beam" or j.Name == "Attachment" then
					j:Destroy();
				end
			end
		end
	end
	for i,v in pairs(char['HumanoidRootPart']:GetChildren()) do
		if v.Name == "Beam" or v.Name == "Attachment" then
			v:Destroy();
		end
	end
end

function ESP(z)
	if z then
		createDistanceLines(char['HumanoidRootPart'],z['HumanoidRootPart']);
		for i,v in pairs(z:GetChildren()) do
			if v:IsA("BasePart") then
				createFaces(v);
			end
		end
		for i,v in pairs(game.Players:GetChildren()) do
			if workspace[v.Name] then
				createDistanceLines(char['HumanoidRootPart'],workspace[v.Name]['HumanoidRootPart'],true);
				for i,b in pairs(workspace[v.Name]:GetChildren()) do
					if v.Name ~= plr.Name then
						if b:IsA("BasePart") then
							createFaces(b,true);
						end
					end
				end
			end
		end
	else
		for i,v in pairs(zombie_storage:GetChildren()) do
			destroyFaces(v);
		end
		for i,v in pairs(game.Players:GetChildren()) do
			if workspace[v.Name] then
				destroyFaces(workspace[v.Name]);
			end
		end
	end
end

workspace.ChildAdded:Connect(function(h)
	for i,v in pairs(game.Players:GetChildren()) do
		if h.Name == v.Name then
			repeat wait(); until workspace[v.Name]:FindFirstChildOfClass("Humanoid");
			if esp_settings.esp then
				createDistanceLines(char['HumanoidRootPart'],workspace[h.Name]['HumanoidRootPart'],true);
				for i,j in pairs(workspace[h.Name]:GetChildren()) do
					if j:IsA("BasePart") then
						createFaces(j,true);
					end
				end
			end
		end
	end
end)

zombie_storage.ChildAdded:Connect(function(h)
	repeat wait(); until h:FindFirstChildOfClass("Humanoid");
	if esp_settings.esp then
		createDistanceLines(char['HumanoidRootPart'],h['HumanoidRootPart']);
	end
	if hide_zombie_names then
		local hum = h:FindFirstChildOfClass("Humanoid");
		hum.DisplayDistanceType = "None";
	end
	for i,v in pairs(h:GetChildren()) do
		if v:IsA("Part") or v:IsA("MeshPart") then
			if esp_settings.esp then
				createFaces(v);
			end
		end
	end
end)

function smoothRGB()
	local botBar = plr.PlayerGui:WaitForChild("Apache")['Frame']['BottomBar'];
	local topBar = plr.PlayerGui:WaitForChild("Apache")['Frame']['TopBar'];
	for h=0,1,0.003 do
		if rgb_settings.rgb then
			local increment = 0.5;
			local r = (math.sin(workspace.DistributedGameTime/2)/2) + increment;
			local g = (math.sin(workspace.DistributedGameTime)/2) + increment;
			local b = (math.sin(workspace.DistributedGameTime*1.5)/2) + increment;
			local color = Color3.new(r,g,b);
			topBar.BackgroundColor3 = color;
			botBar.BackgroundColor3 = color;
		else
			topBar.BackgroundColor3 = menu_settings.menu_color;
			botBar.BackgroundColor3 = menu_settings.menu_color;
		end
		wait();
		if rgb_settings.rgb then
			smoothRGB();
		end
	end
end

function hackLoader(hack)
	if hack == "[chams]" then
		if not esp_settings.esp then
			esp_settings.esp = true;
			for i,v in pairs(zombie_storage:GetChildren()) do
				ESP(v);
			end
		else
			esp_settings.esp = false;
			ESP();
		end
	end
	if hack == "[rgb_topbar]" then
		if not smooth_rgb then
			smooth_rgb = true;
			spawn(function()
				smoothRGB();
			end)
		else
			smooth_rgb = false;
		end
	end
	if hack == "[hide_names]" then
		if not hide_zombie_names then
			hide_zombie_names = true;
			removeZombieNames(true);
		else
			hide_zombie_names = false;
			removeZombieNames();
		end
	end
	if hack == "[noclip]" then
		if not flyhack_settings.flyhack then
			flyhack_settings.flyhack = true;
			flyHack();
		else
			flyhack_settings.flyhack = false;
			flyHack();
		end
	end
	if hack == "[promod]" then
		if not promod_settings.promod then
			promod_settings.promod = true;
			proMod(true);
		else
			promod_settings.promod = false;
			proMod();
		end
	end
	if hack == "[fullbright]" then
		if not fullbright then
			fullbright = true;
			graphicsMode(true);
		else
			fullbright = false;
			graphicsMode();
		end
	end
	if hack == "[super_speed]" then
		if not super_speed_settings.super_speed then
			super_speed_settings.super_speed = true;
			superSpeed(true);
		else
			super_speed_settings.super_speed = false;
			superSpeed();
		end
	end
	if hack == "[super_jump]" then
		if not super_jump_settings.super_jump then
			super_jump_settings.super_jump = true;
			superJump(true);
		else
			super_jump_settings.super_jump = false;
			superJump();
		end
	end
end

function initializeMenu()
	local UI = Instance.new("ScreenGui");
	UI.Parent = plr.PlayerGui;
	UI.Name = "Apache";
	local MainFrame = Instance.new("Frame");
	MainFrame.Parent = UI;
	MainFrame.BackgroundColor3 = Color3.fromRGB(255,255,255);
	MainFrame.BackgroundTransparency = 0;
	MainFrame.BorderSizePixel = 0;
	MainFrame.Size = UDim2.new(0,188,0,313);
	MainFrame.Position = UDim2.new(0,20,0,40);
	MainFrame.Active = true;
	MainFrame.Draggable = true;
	local TopBar = Instance.new("ImageLabel");
	TopBar.Parent = MainFrame;
	TopBar.BackgroundColor3 = menu_settings.menu_color;
	--TopBar.Image = "rbxassetid://2851926732";
	--TopBar.BackgroundColor3 = menu_settings.menu_color;
	--TopBar.BackgroundTransparency = 1;
	TopBar.Position = UDim2.new(-0,0,-0.058,0);
	TopBar.Size = UDim2.new(0,188,0,49);
	TopBar.ScaleType = "Slice";
	TopBar.SliceScale = 1;
	TopBar.SliceCenter = Rect.new(12, 12, 12, 12);
	TopBar.BorderSizePixel = 0;
	TopBar.Name = "TopBar";
	local Ignore = Instance.new("Frame");
	Ignore.Parent = MainFrame;
	Ignore.Size = UDim2.new(0,188,0,46);
	Ignore.Position = UDim2.new(-0,0,0.048,0);
	Ignore.BackgroundColor3 = Color3.fromRGB(255,255,255);
	Ignore.BorderSizePixel = 0;
	local Scroller = Instance.new("ScrollingFrame");
	Scroller.Parent = MainFrame;
	Scroller.Size = UDim2.new(0,170,0,280);
	Scroller.Position = UDim2.new(0.043,0,0.073,0);
	Scroller.BackgroundColor3 = Color3.fromRGB(232,232,232);
	Scroller.BorderSizePixel = 1;
	local Options = Instance.new("Folder");
	Options.Parent = UI;
	Options.Name = "Options";
	local Template = Instance.new("Folder");
	Template.Parent = MainFrame;
	Template.Name = "Template";
	local TemplateOption = Instance.new("TextLabel");
	TemplateOption.Name = "TemplateOption";
	TemplateOption.Parent = Template;
	TemplateOption.BackgroundColor3 = menu_settings.menu_leave_color;
	TemplateOption.BackgroundTransparency = 0;
	TemplateOption.BorderSizePixel = 0;
	TemplateOption.TextColor3 = Color3.fromRGB(0,0,0);
	TemplateOption.Font = menu_settings.menu_font;
	TemplateOption.Size = UDim2.new(0,157,0,30);
	TemplateOption.TextSize = 15;
	TemplateOption.TextStrokeTransparency = 1;
	TemplateOption.TextXAlignment = "Right";
	TemplateOption.Position = UDim2.new(0,0,0,0);
	TemplateOption.Visible = false;
	local TemplateCheckBox = Instance.new("TextButton");
	TemplateCheckBox.Name = "CheckBox";
	TemplateCheckBox.Parent = TemplateOption;
	TemplateCheckBox.BackgroundColor3 = Color3.fromRGB(255,255,255);
	TemplateCheckBox.BackgroundTransparency = 0;
	TemplateCheckBox.BorderSizePixel = 1;
	TemplateCheckBox.Text = "";
	TemplateCheckBox.Size = UDim2.new(0,20,0,20);
	TemplateCheckBox.Position = UDim2.new(0.051,-3,0.167,0);
	TemplateCheckBox.TextColor3 = Color3.fromRGB(0,0,0);
	TemplateCheckBox.TextSize = 17;
	local BottomBar = Instance.new("TextLabel");
	BottomBar.Parent = MainFrame;
	BottomBar.BackgroundColor3 = menu_settings.menu_color;
	BottomBar.Visible = true;
	BottomBar.Size = UDim2.new(0,188,0,27);
	BottomBar.Position = UDim2.new(0,0,1,0);
	BottomBar.BorderSizePixel = 0;
	BottomBar.Font = menu_settings.menu_font;
	BottomBar.TextColor3 = Color3.fromRGB(255,255,255);
	BottomBar.Text = "[apache,by_jord404]";
	BottomBar.TextSize = 15;
	BottomBar.Name = "BottomBar";
	--BottomBar.TextXAlignment = "Left";
	local Settings = Instance.new("ImageButton");
	Settings.Parent = TopBar;
	Settings.Image = menu_settings.menu_settings_icon;
	Settings.Size = UDim2.new(0,20,0,20);
	Settings.BackgroundTransparency = 1;
	Settings.Position = UDim2.new(0.894,-7,0,7);
	local ColorPanel = Instance.new("ScrollingFrame");
	ColorPanel.Parent = MainFrame;
	ColorPanel.Size = UDim2.new(0,170,0,280);
	ColorPanel.Position = UDim2.new(0.043,0,0.073,0);
	ColorPanel.BackgroundColor3 = Color3.fromRGB(232,232,232);
	ColorPanel.Visible = false;
	local colorOption = Instance.new("TextButton");
	colorOption.Name = "colorOption";
	colorOption.Parent = Template;
	colorOption.BackgroundColor3 = menu_settings.menu_leave_color;
	colorOption.BackgroundTransparency = 0;
	colorOption.BorderSizePixel = 0;
	colorOption.TextColor3 = Color3.fromRGB(0,0,0);
	colorOption.Font = menu_settings.menu_font;
	colorOption.Size = UDim2.new(0,157,0,30);
	colorOption.TextSize = 15;
	colorOption.TextStrokeTransparency = 1;
	colorOption.TextXAlignment = "Right";
	colorOption.Position = UDim2.new(0,0,0,0);
	colorOption.Visible = false;
	colorOption.Text = "";
	local UILL = Instance.new("UIListLayout");
	UILL.Parent = Scroller;
	UILL.FillDirection = "Vertical";
	UILL.HorizontalAlignment = "Left";
	UILL.SortOrder = "LayoutOrder";
	UILL.VerticalAlignment = "Top";
	UILL:Clone().Parent = ColorPanel;
	for i,v in pairs(menu_color_names) do
		local color = colorOption:Clone();
		color.Parent=ColorPanel;
		color.Visible=true;
		color.Name = v;
	end
	for i,v in pairs(ColorPanel:GetChildren()) do
		if v:IsA("TextButton") then
			v.BackgroundColor3 = menu_color_opts[v.Name];
		end
	end
	local rgbOption = TemplateOption:Clone();
	rgbOption.Parent = ColorPanel;
	rgbOption.Visible = true;
	rgbOption.Text = "[smooth_rgb]".." ";
	rgbOption.Name = "RGB";
	for i,v in pairs(ColorPanel:GetChildren()) do
		if v:IsA("TextButton") then
			v.MouseButton1Click:Connect(function()
				if not rgb_settings.rgb then
					TopBar.BackgroundColor3 = menu_color_opts[v.Name];
					BottomBar.BackgroundColor3 = menu_color_opts[v.Name];
					menu_settings.menu_color = menu_color_opts[v.Name];
				end
			end)
		end
		if v:IsA("TextLabel") then
			v['CheckBox'].MouseButton1Click:Connect(function()
				if v.Text == "[smooth_rgb] " then
					if not rgb_settings.rgb then
						rgb_settings.rgb = true;
						v['CheckBox'].Text = checkbox_settings.tik;
						v['CheckBox'].TextColor3 = checkbox_settings.tik_c;
						smoothRGB();
					else
						rgb_settings.rgb = false;
						v['CheckBox'].Text = checkbox_settings.null;
						v['CheckBox'].TextColor3 = checkbox_settings.null_c;
					end
				end
			end)
		end
	end
	Settings.MouseButton1Click:Connect(function()
		if not menu_settings.menu_in_settings then
			menu_settings.menu_in_settings = true;
			Settings.Image = menu_settings.menu_color_close;
			ColorPanel.Visible = true;
		else
			menu_settings.menu_in_settings = false;
			Settings.Image = menu_settings.menu_settings_icon;
			ColorPanel.Visible = false;
		end
	end)
	Settings.MouseEnter:Connect(function()
		--[[ ]]
	end)
	local Title = Instance.new("TextLabel");
	Title.Parent = TopBar;
	Title.BackgroundTransparency=1;
	Title.TextSize = 15;
	Title.Font = menu_settings.menu_font;
	Title.TextColor3 = Color3.fromRGB(255,255,255);
	Title.Position = UDim2.new(0.043,0,0,0);
	Title.Size = UDim2.new(0,179,0,33);
	Title.TextXAlignment = "Left";
	local TickSound = Instance.new("Sound")
	TickSound.Parent = UI;
	TickSound.SoundId = menu_settings.tick_sound;
	local HoverSound = Instance.new("Sound")
	HoverSound.Parent = UI;
	HoverSound.SoundId = menu_settings.hover_sound;
	
	local optNum = 0;
	
	for i,v in pairs(menu_options) do
		optNum = optNum + 1;
		local optFolder = Instance.new("Folder");
		optFolder.Parent = Options;
		optFolder.Name = v;
		local toggleCheck = Instance.new("BoolValue");
		toggleCheck.Name = "toggle";
		toggleCheck.Parent = optFolder;
		local optNumber = Instance.new("NumberValue");
		optNumber.Name = "num";
		optNumber.Parent = optFolder;
		optNumber.Value = optNum;
	end
	
	local optCount = 0;
	
	for i,v in pairs(Options:GetChildren()) do
		local option = TemplateOption:Clone();
		option.Parent=Scroller;
		option.Visible=true;
		option.Text = v.Name.." ";
		option.Name = v.Name;
		optCount = optCount +1;
	end
	
	Title.Text = "[0/"..optCount.."]"
	
	local optionsSelected = 0;
	
	for i,v in pairs(Scroller:GetChildren()) do
		if v:IsA("TextLabel") and v['CheckBox'] then
			v['CheckBox'].MouseButton1Click:Connect(function()
				if Options[v.Name]['toggle'].Value then
					optionsSelected = optionsSelected - 1;
					Title.Text = "["..optionsSelected.."/"..optCount.."]";
					Options[v.Name]['toggle'].Value = false;
					v['CheckBox'].Text = checkbox_settings.null;
					v['CheckBox'].TextColor3 = checkbox_settings.null_c;
					if not menu_settings.menu_in_settings then
						TickSound:Play();
					end
					hackLoader(v.Name);
				else
					optionsSelected = optionsSelected + 1;
					Title.Text = "["..optionsSelected.."/"..optCount.."]";
					Options[v.Name]['toggle'].Value = true;
					v['CheckBox'].Text = checkbox_settings.tik;
					v['CheckBox'].TextColor3 = checkbox_settings.tik_c;
					if not menu_settings.menu_in_settings then
						TickSound:Play();
					end
					hackLoader(v.Name);
				end
			end)
		end
	end
	
	for i,v in pairs(Scroller:GetChildren()) do
		if v:IsA("TextLabel") then
			v.MouseEnter:Connect(function()
				if not menu_settings.menu_in_settings then
					HoverSound:Play();
				end
				--Title.Text = Options[v.Name]["num"].Value.."/"..optCount;
				v.BackgroundColor3 = menu_settings.menu_highlight_color
			end)
		end
	end
	
	for i,v in pairs(Scroller:GetChildren()) do
		if v:IsA("TextLabel") then
			v.MouseLeave:Connect(function()
				v.BackgroundColor3 = menu_settings.menu_leave_color;
			end)
		end
	end
	
	char['Humanoid'].Died:Connect(function()
		for i,v in pairs(Scroller:GetChildren()) do
			if v:IsA("TextLabel") and v['CheckBox'] then
				v['CheckBox'].Text = checkbox_settings.null;
				v['CheckBox'].TextColor3 = checkbox_settings.null_c;
			end
		end
		for i,v in pairs(Options:GetChildren()) do
			v['toggle'].Value = false;
		end
		flyhack_settings.flyhack = false;
		esp_settings.esp = false;
		hide_zombie_names = false;
		smooth_rgb = false;
		ESP();
		removeZombieNames();
		optNum = 0;
		optCount = 0;
		UI:Destroy();
	end)
	
end

initializeMenu();
