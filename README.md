# Mainline-Mesa-Experimental

--One mainline mesa experimental open source radeon gpu out performs 58% better than two windows 10 (finalized stock driver) crossfire radeon gpu's

This repository provides the instructions on how to compile mainline mesa with experimental compilers and unsupported optimisations for the best/fastest possible working frame rate. I'd anticipate this would be appealing to an audience of gamers, top benchmark enthusiasts or possibly the mesa 3d dev's looking forward to doing something like adding new features as experimental compilers become supported and stable. See the detailed benchmarks at https://github.com/jjaxse2017/Mainline-Mesa-Expermental/blob/master/detailed%20benchmarks

Goto the release page for the compile instructions/files at https://github.com/jjaxse2017/Mainline-Mesa-Expermental/releases and download https://github.com/jjaxse2017/Mainline-Mesa-Expermental/releases/download/1.0/mesa.mainline.expermental.tar.gz. A bonus Mesa 13.0-dev used to benchmark the winning amd drivers are linked to the release, anyone with other cards, I'd be happy about the results.

<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html><head>

<h1>Unigine Heaven Benchmark 4.0 -- Ubuntu 17.04 Single GPU linux mesa 13.0-dev</h1>
<table class="result">
<tr><td class="right">FPS:</td><td><div class="orange"><strong>88.9</strong></div></td></tr>
<tr><td class="right">Score:</td><td><div class="orange"><strong>2240</strong></div></td></tr>
<tr><td class="right">Min FPS:</td><td><div class="orange"><strong>32.6</strong></div></td></tr>
<tr><td class="right">Max FPS:</td><td><div class="orange"><strong>157.6</strong></div></td></tr>
</table>
<h2>System</h2>
<table class="detail">
<tr><td class="right">Platform:</td><td><div class="highlight">Linux 4.14.0-999-generic x86_64</div></td></tr>
<tr><td class="right">CPU model:</td><td><div class="highlight">Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz (3829MHz) x2</div></td></tr>
<tr><td class="right">GPU model:</td><td><div class="highlight">AMD Radeon HD 5800 Series (1024MB) x1</div></td></tr>
</table>
<h2>Settings</h2>
<table class="detail">
<tr><td class="right">Render:</td><td><div class="highlight">OpenGL</div></td></tr>
<tr><td class="right">Mode:</td><td><div class="highlight">1680x1050 8xAA windowed</div></td></tr>
<tr><td class="right">Preset</td><td><div class="highlight">Custom</div></td></tr>
<tr><td class="right">Quality</td><td><div class="highlight">High</div></td></tr>
<tr><td class="right">Tessellation:</td><td>Disabled</td></tr>
</table>
<div class="engine">Powered by <a href="http://unigine.com/products/unigine/">UNIGINE Engine</a></div>
<div class="copyright"><a href="http://unigine.com/">Unigine Corp.</a> &copy; 2005-2013</div>
</body></html>


<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html><head>

<h1>Unigine Heaven Benchmark 4.0 -- Crossfire windows 10 latest ATI/AMD driver</h1>
<table class="result">
<tr><td class="right">FPS:</td><td><div class="orange"><strong>56.4</strong></div></td></tr>
<tr><td class="right">Score:</td><td><div class="orange"><strong>1422</strong></div></td></tr>
<tr><td class="right">Min FPS:</td><td><div class="orange"><strong>8.6</strong></div></td></tr>
<tr><td class="right">Max FPS:</td><td><div class="orange"><strong>99.5</strong></div></td></tr>
</table>
<h2>System</h2>
<table class="detail">
<tr><td class="right">Platform:</td><td><div class="highlight">Windows NT 6.2 (build 9200) 64bit</div></td></tr>
<tr><td class="right">CPU model:</td><td><div class="highlight">Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz (3829MHz) x2</div></td></tr>
<tr><td class="right">GPU model:</td><td><div class="highlight">AMD Radeon HD 5800 Series 15.201.1151.1008 (1024MB) x2</div></td></tr>
</table>
<h2>Settings</h2>
<table class="detail">
<tr><td class="right">Render:</td><td><div class="highlight">Direct3D11</div></td></tr>
<tr><td class="right">Mode:</td><td><div class="highlight">1680x1050 8xAA fullscreen</div></td></tr>
<tr><td class="right">Preset</td><td><div class="highlight">Custom</div></td></tr>
<tr><td class="right">Quality</td><td><div class="highlight">High</div></td></tr>
<tr><td class="right">Tessellation:</td><td>Disabled</td></tr>
</table>
<div class="engine">Powered by <a href="http://unigine.com/products/unigine/">UNIGINE Engine</a></div>
<div class="copyright"><a href="http://unigine.com/">Unigine Corp.</a> &copy; 2005-2013</div>
</body></html>
