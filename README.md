#### Scripting/Customization Docs
[Customizing](http://www.soundspectrum.com/whitecap/Documentation/customizing.html)

[Scripting](http://www.soundspectrum.com/whitecap/Documentation/scripting.html)

[Config Programming](http://www.soundspectrum.com/whitecap/Documentation/config-programming.html)

[Version History](http://www.soundspectrum.com/whitecap/Documentation/version-history.html)

###DOCUMENTATION

#### Customizing

<table>
                            <tbody><tr>
                                <td width="20">&nbsp;</td>
                                <td align="left" height="25" class="header_orange" valign="top">Customizing WhiteCap</td>
                                <td width="20">&nbsp;</td>
                            </tr>
                            <tr>
                                <td width="20">&nbsp;</td>
                                <td align="left" class="text" valign="top">
									<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;You can customize WhiteCap by editing its preferences file or by writing
								    scripts. The preferences file and script files are <em><strong>plain-text files</strong></em> and
								    end with ".txt". If you edit one of these files, you must <em><strong>resave them as plain-text</strong></em>.
								    Otherwise, WhiteCap will not be able to process them. For example,  OS X’s <em>TextEdit</em> saves
								    files as Rich Text Format (.rtf) by default, so you must designate your file as plain-text
								    (in the <strong>Format</strong> menu),
								    and save it as a .txt file. In Windows, <em>Notepad</em> and <em>WordPad</em> are both effective text editors
								    (but note that non-DOS style text files won’t appear properly in Notepad—try opening and then resaving
								    them in WordPad). Alternatively, there are also many excellent shareware text editors
								    publicly available that are also suitable. Whatever text editor you do use, it’s recommended that you disable
								    line wrapping for readability. Disabling line wrapping also prevents you mistaking wrapped
								    lines for new lines. </p>
                                    <dl>
                                        <br>
                                        <dt><b>The Preferences File</b></dt>
                                    </dl>
                                    <p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The WhiteCap preferences file is  a <strong><em>plain-text</em></strong> file
                                        containing a list of values (in no particular order). The purpose of the preferences
                                        file is to allow various user variables (ex, window position, full screen resolution,
                                        visual reactivity settings) to persist from each time WhiteCap is run to the
                                        next. Since WhiteCap only writes/updates its preferences file when it exits,
                                        you must run and exit WhiteCap at least once before you’ll be able find it.  On Windows,  preference files are located in C:\Documents
                                        and Settings\Application Data\SoundSpectrum\WhiteCap" and on Mac OS X, they are located
                                        in "~/Library/Preferences/SoundSpectrum/WhiteCap". </p>
									<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;If you modify the preferences file while WhiteCap is running, then your changes will be overwritten when WhiteCap exits (so you should modify it when WhiteCap is <em>not</em> running). An example of when you would edit the preferences file would be if your media player didn’t support keystrokes or the pref that you want to edit is not accessible via key commands.  If you have the option to edit either the preferences file or the boot file in order to change something, it’s better to edit the preferences file rather than the boot file. A mistake in the preferences file can always be corrected by deleting the preferences file, but a mistake in the boot file can only be corrected by replacing it with the original boot file (ie. reinstallation). Finally, if WhiteCap behaves strangely after you edit its preferences file, it’s likely that you inadvertently caused a problem.  If this is the case, simply delete the preferences file.  When you delete it (when WhiteCap isn’t running), a new "factory" preferences file will be created the next time WhiteCap starts up. The following is a list of all the parameters found in the WhiteCap preferences file:<br>
                                    <br>
                                    </p>
                                    <table width="95%" border="1" align="center" cellpadding="3" cellspacing="0" bordercolor="#5F5D5E">
                                        <tbody><tr align="center">
                                            <td colspan="2" class="textbold">'Preferences ([PlayerName]).txt'</td>
                                        </tr>

                                        <tr>
                                            <td class="textbold">Audio.InputSource</td>
                                            <td class="text">This specifies the name of the audio input source to be visualized.  If the name is blank or cannot be found in the list of available audio sources, the best audio input source is used.  This pref is only used when WhiteCap isn't running inside a media player. </td>
                                        </tr>

                                        <tr>
                                            <td class="textbold">Audio.FFT.Params</td>
                                            <td class="text">These params specify the behavior the FFT auto-normalization
                                                subsystem.</td>
                                        </tr>
                                        
                                        <tr>
                                            <td class="textbold">Audio.AutoDetect.Enabled<br>Audio.AutoDetect.SilenceThreshold<br>Audio.AutoDetect.Wait</td>
                                            <td class="text">When enabled and applicable, if the time period specified by <em>AutoDetect.Wait</em> elapses with no audio activity below the level specified in <em>AutoDetect.SilenceThreshold</em>, WhiteCap will automatically scan other audio input sources for signs of audio activity.  If it finds another active audio input source, it will use that source until the primary source breaks the silence threshold.  This, for example, is useful in screen saver mode since any number of audio sources may be of interest to use for audio input.  </td>
                                        </tr>
                                        
                                        <tr>
                                            <td class="textbold">Audio.FFT.Smooth</td>
                                            <td class="text">As this value increases, the smoothing of fft(0..1) increases proportionally (ie, peaks and valleys will be less jagged).  Doubling/Halving this number will double/half the amount of smoothing.</td>
                                        </tr>
                                        
                                        <tr>
                                            <td class="textbold">Audio.FFT.NumBins</td>
                                            <td class="text">This defines how many values/elements are in fft(0..1). As <em>Audio.FFT.NumBins</em> increases, the frequency spectrum will be divided up into more "bins" (a "bin" is defined as the average value of a small sub-section of a frequency spectrum, like how a bucket or pail collects a footprint of rain and not a point). In a config file, you can access <em>Audio.FFT.NumBins</em> by using NUM_FFT_BINS. See the documentation in the example configs, especially the documentation of the Stps parameter in "Rotating Corridor".</td>
                                        </tr>
                                        
                                        <tr>
                                            <td class="textbold">Audio.PCM.Smooth</td>
                                            <td class="text">As this value increases, the more mag(0..1) is smoothed (ie, peaks and valleys will be less jagged). Approximately doubling/halving this number will double/half the amount of smoothing.</td>
                                        </tr>
                                        
                                        <tr>
                                            <td class="textbold">Audio.PCM.NumBins</td>
                                            <td class="text">Similar to <em>Audio.FFT.NumBins</em>, this parameter specifies how many elements are in each sound sample (that is, how many elements make up mag(0..1)). PCM stands for "pulse code modulation" which just means a sequence of amplitude values that correspond to the position of a recording membrane. A "sample" is slang for a sequence of amplitude values that form a short clip of audio—in other words a "sample" is slang for a recorded audio segment. <em>Audio.PCM.NumBins</em> defines how many steps is in mag(0..1). In a config file, you can access <em>Audio.PCM.NumBins</em> with the global variable NUM_SAMPLE_BINS.</td>
                                        </tr>
                                        
                                        <tr>
                                            <td class="textbold">Audio.Response.Scale</td>
                                            <td class="text">Specifies the scale of the fft and pcm audio data that's visualized.
                                            </td>
                                        </tr>
                                        
                                        <tr>
                                            <td class="textbold">Fullscreen.Device</td>
                                            <td class="text">This specifies the display device that WhiteCap will attempt to use for full screen mode. The value is such that the main/primary device is 0, the next is 1, the next is 2, and so on. If this value is -1 (ie, SS_HOST_DISPLAY_DEVICE), then the display device that WhiteCap will attempt to use for full screen mode will be whatever the display device currently hosting the WhiteCap window. <em>Note: this is not available for all media players (because most media players don’t allow a plugin to request a specific display device for full screen mode). </em></td>
                                        </tr>
                                        
                                        <tr>
                                            <td class="textbold">Graphics.TargetFrameRate</td>
                                            <td class="text">WhiteCap will attempt to maintain a frame rate that matches the value specified in this pref. If WhiteCap has a frame rate below what you specify, it’s because (a) your system isn’t fast enough to achieve the desired frame rate for the current frame dimensions, or (b) the host media player is electing not to have WhiteCap draw as often as possible. At this point, only decreasing the frame size, exiting other applications, or switching media players can increase frame rate.<br><br>

Note that some media players only call a visual plugin a maximum number of times per second (and nothing can be done to change that other than abandon that media player). Also note that it takes a couple seconds for WhiteCap to stabilize on the target frame rate when a step-change in load occurs (e.g. when a much less intensive config starts).</td>
                                        </tr>
                                        
                                         <tr>
                                            <td class="textbold">Graphics.PreventDisplaySleep</td>
                                            <td class="text">If set, WhiteCap will ask the OS to prevent display device sleep when WhiteCap is in fullscreen mode.</td>
                                        </tr>
                                        
                                        <tr>
                                            <td class="textbold">WaveShape.LineWidth.Offset<br>WaveShape.LineWidth.Scale</td>
                                            <td class="text">The value of these parameters affect the
                                                line thickness of all drawn lines. All line thicknesses are multiplied by
                                                <em>LineWidth.Scale</em> and then <em>LineWidth.Offset</em> is added. On G-Force, note that
                                                excessively increasing line thickness can cause color saturation (depending
                                                on the current FlowField), causing the entire screen to be flooded with an
                                                excess of foreground color. See also <em>WaveShape.AutoLineScale</em>.</td>
                                        </tr>
                                        
                                        <tr>
                                            <td class="textbold">WaveShape.AutoLineScale</td>
                                            <td class="text">When this value is non-zero, following
                                                a frame resize, <em>WaveShape.LineWidth.Scale</em> is set to a value proportional to the
                                                new frame size. In effect, the ratio of pixels from line drawing to total
                                                pixels becomes roughly constant. </td>
                                        </tr>
                                        
                                        <tr>
                                            <td class="textbold">TrackText.Auto</td>
                                            <td class="text">If this value is non-zero, track text (and album cover art,
                                                if available) will be automatically displayed when the currently playing
                                                track/song changes. If this value is zero, track text and album cover art
                                                will never appear automatically. </td>
                                        </tr>
                                        
                                        <tr>
                                            <td class="textbold">TrackText.Duration</td>
                                            <td class="text">The number of seconds track text (and album cover art, if available) will remain visible after it appears. By default, track text (and album cover art) will appear when a new track begins or when ’T’ is pressed. </td>
                                        </tr>
                                        
										<tr> 
                                            <td class="textbold">TrackText.Animation</td>
                                            <td class="text">The name of the TrackAnimation config to be run when a new track starts in the host audio player.  Look in Packages/Common.TrackAnimation.package to make your own or modify existing animations.
                                            </td>
                                        </tr>
                                        
                                        <tr>
                                            <td class="textbold">TrackText.Font</td>
                                            <td class="text">Specifies the font family used for track text animations.</td>
                                        </tr>
                                        
                                        <tr>
                                            <td class="textbold">TrackText.Size</td>
                                            <td class="text">Specifies the font size used for track text animations.</td>
                                        </tr>

                                        <tr>
                                            <td class="textbold">Prefs.Version</td>
                                            <td class="text">Stores the version of the prefs file and is how WhiteCap can identify an out-of-date prefs file (if this value is below the "compatible" version number, WhiteCap will use internally stored "factory" pref values). You will never normally need to edit this value (and using an invalid or out-of-date prefs file with the "current" WhiteCap version number could cause WhiteCap to crash or operate improperly). </td>
                                        </tr>
                                        
                                        <tr>
                                            <td class="textbold">UI.ActivateOnChars</td>
                                            <td class="text">Specifies the set of characters that toggle/activate the UI.</td>
                                        </tr>

                                        <tr>
                                            <td class="textbold">UI.ActivateOnClick</td>
                                            <td class="text">If set, the UI will activate on a user click in the WhiteCap window.</td>
                                        </tr>

                                        <tr>
                                            <td class="textbold">UI.Font</td>
                                            <td class="text">Specifies the font name used in the on-screen UI.</td>
                                        </tr>
                                        
                                        <tr>
                                            <td class="textbold">UI.MinSize</td>
                                            <td class="text">Specifies the minimum height and width of the UI.  If the frame
                                                size is less than this size, the UI will scale itself to retain the minimum
                                                size virtually.</td>
                                        </tr>
                                        
                                        <tr>
                                            <td class="textbold">UI.Timeout</td>
                                            <td class="text">Specifies the number of seconds the UI should remain visible once the user is idle.</td>
                                        </tr>
                                        
                                        <tr>
                                            <td class="textbold">Window.top<br>Window.left<br>Window.bottom<br>Window.right</td>
                                            <td class="text">Stores the position of the WhiteCap window in global screen coordinates. Note that when WhiteCap runs under certain media players, these parameters aren’t used because the host media player manages the rectangle size and position, not WhiteCap.</td>
                                        </tr>
                                        
                                        <tr>
                                            <td class="textbold">[ConfigType].<br>ConfigPrepTime</td>
                                            <td class="text">Specifies the number of seconds a config should be given to perform any background calculations or prep.</td>
                                        </tr>
                                        <tr>
                                            <td class="textbold">[ConfigType].<br>Slideshow.EnableOnStartup</td>
                                            <td class="text">If non-zero, the given config set's slideshow mode is enabled when WhiteCap starts up.</td>
                                        </tr>
                                        <tr>
                                            <td class="textbold">[ConfigType].<br>Slideshow.Interval.Duration</td>
                                            <td class="text">The number of seconds between when a config slideshow change completes to when the next config change commences.</td>
                                        </tr>
                                        <tr>
                                            <td class="textbold">[ConfigType].<br>Slideshow.Interval.Duration.Deviation</td>
                                            <td class="text">Specifies the standard deviation of the slideshow interval duration specified by <em>Interval.Duration.Deviation</em>.  A value of .1 if Slideshow.Interval.Duration is set to 15 seconds means that there's a random standard deviation of 1.5 seconds for each successive slideshow interval that is calculated.</td>
                                        </tr>
                                        <tr>
                                            <td class="textbold">[ConfigType].<br>Transition.Duration</td>
                                            <td class="text">Specifies the number of seconds that WhiteCap will spend transitioning from one config to the next when the slideshow mode is enabled for the given config type and the config slideshow interval elapses.</td>
                                        </tr>
                                        <tr>
                                            <td class="textbold">[ConfigType].<br>Transition.Duration.Quick</td>
                                            <td class="text">Specifies the number of seconds that WhiteCap will spend transitioning from one config to the next when the user manually initiates a config change (typically a via keyboard).</td>
                                        </tr>
                                        <tr>
                                            <td class="textbold">[ConfigType].<br>Transition.Duration.Deviation</td>
                                            <td class="text">Specifies the standard deviation of the slideshow transpiration
                                                duration specified by Transition.Duration.Deviation.</td>
                                        </tr>
                                        <tr>
                                            <td class="textbold">[ConfigType].<br>Transition.Function</td>
                                            <td class="text">Specifies the mapping of a uniformly changing scalar (t, that
                                                starts at 0.0 when a config transition starts and 1.0 when it ends) to a
                                                weight that specifies how much of the oncoming config to use. This expression
                                                must always evaluate to 0 when t = 0 and evaluate to 1 when t = 1. If a transition
                                                is 10 seconds long, t will be .2 after 2 seconds. Typical transition weight
                                                functions start with linear change but finish with a decreasing rate of change,
                                                offering the visual aesthetic of gliding into 1.0. Try graphing the function <em>y=1-(1-x)^1.5</em> to
                                                see an example</td>
                                        </tr>

                                        
                                        


                                            </tbody></table>
                                    
                                    
                                    <br>&nbsp;<br>
                                    <table width="95%" border="1" align="center" cellpadding="3" cellspacing="0" bordercolor="#5F5D5E">
                                        <tbody><tr align="center">
                                            <td colspan="2" class="textbold">'Global Preferences.txt'</td>
                                        </tr>
                                        <tr>
                                            <td class="textbold">Graphics.Direct3D.Disabled</td>
                                            <td class="text">(Windows only) If non-zero, the visual
                                                engine will attempt to render using OpenGL instead of Direct3D. If the engine
                                                is unable to run without using Direct3D (e.g. due to limited OpenGL drivers), setting this pref could result in
                                                blank output from WhiteCap.</td>
                                        </tr>
                                        <tr>
                                            <td class="textbold">Graphics.Quality</td>
                                            <td class="text">This is accessed by python-based configs to help make choices about richer graphical effects that come at the cost of frame rate performance.</td>
                                        </tr>
                                        <tr>
                                            <td class="textbold">Network.Mode</td>
                                            <td class="text">Specifies the class of permitted network connections, allowing WhiteCap to be controlled.  The value 'LocalOnly' specifies that only connections originating from the same machine as the running instance of WhiteCap will be allowed to connect and is the default value for security reasons.  Connections not originating locally are refused. If the value is 'LocalOrRemote', then connections originating from any IP address will be accepted. </td>
                                        </tr>
                                    </tbody></table>
                                    <br>
                                    <br>
                                    
								</td>
                                <td width="20">&nbsp;</td>
                            </tr>
                        </tbody></table>
					</td>
                    <td bgcolor="#5F5D5E" width="1"></td>
                </tr>
                <tr align="center">
                    <td colspan="3"><img src="graphics/605bot.gif" width="605" height="10"></td>
                </tr>
            </tbody></table>
		</td>
</table>
### Scripting

<td valign="top">
			<table width="605" cellspacing="0" cellpadding="0" align="center" bgcolor="#373536">
            	<tbody><tr align="center">
                	<td colspan="3">Scripting WhiteCap</td>
            	</tr>
            	<tr align="center">
                	<td bgcolor="#5F5D5E" width="1"></td>
                	<td width="603" valign="top" align="left">
					<table width="603" cellspacing="0" cellpadding="0" bgcolor="#373536">
  <tbody><tr>
    </table><table>
  </tr>
  <tr>
    <td width="20">&nbsp;</td>
    <td align="left" class="text" valign="top">WhiteCap has scripting services that allow you to automate or design WhiteCap performances. WhiteCap Scripts use a timeline (or "timecode") scheme in order to synchronize WhiteCap events with events that occur at preset times. Several sample scripts come with WhiteCap. If you look inside the folder named "Scripts" and view the files found inside it, you can follow along with what you're seeing when you run the script in WhiteCap. Studying the scripts that come with WhiteCap will teach you how to create your own scripts. See the <a href="../../whitecap/Documentation/customizing.html" class="class3" target="_blank">customizing</a> section for more.<br>
    <br>
    <b>The 2 ways a script can be started:</b>
    <dl>
    <ol>
    <li>A script has the name "CTRL O.py" and <b>CTRL O</b> is pressed.</li>
    <li>The command <span class="textbold">Run( "ScriptName" )</span> is used (extensions are optional).</li>
    </ol>
    </dl>
    <p>&nbsp;</p></td>
    <td width="20">&nbsp;</td>
  </tr>
  <tr>
    <td width="20">&nbsp;</td>
    <td align="left" height="35" class="header_orange" valign="top">Getting Started with Scripting</td>
    <td width="20">&nbsp;</td>
  </tr>
  <tr>
    <td width="20">&nbsp;</td>
    <td align="left" height="25" class="text" valign="top">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;In order to write your own scripts, you'll need to know what commands are available and how to invoke them. In the <span class="textbold">Scripts</span> folder, you'll find the file "Script Command Reference.py", which documents and describes common script commands.
    <p><span class="textbold">Note:</span> the scripting documentation is under construction and is evolving as WhiteCap develops. It's recommended you study the example script files to get a basic understanding of scripting and command usage.<br><br></p>
    </td>
    <td width="20">&nbsp;</td>
  </tr>
</tbody></table>					</td>
                	<td bgcolor="#5F5D5E" width="1"></td>
            	</tr>
            	<tr align="center">
                	<td colspan="3"><img src="graphics/605bot.gif" width="605" height="10"></td>
            	</tr>
        	</tbody></table>
