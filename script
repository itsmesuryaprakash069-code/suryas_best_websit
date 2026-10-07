// Mobile menu
const menu = document.querySelector('.menu'), nav = document.getElementById('nav');
menu.addEventListener('click', () => {
  const open = nav.classList.toggle('open');
  menu.setAttribute('aria-expanded', open);
});
nav.addEventListener('click', e => { if (e.target.tagName === 'A') { nav.classList.remove('open'); menu.setAttribute('aria-expanded', false); } });

// Hero: a C program that "builds" the site, typed once on load
const lines = [
  '<span class="c">// site.c: how I build your website</span>',
  '<span class="k">#include</span> <span class="s">&lt;design.h&gt;</span>',
  '<span class="k">#include</span> <span class="s">&lt;speed.h&gt;</span>',
  '',
  '<span class="k">int</span> main(<span class="k">void</span>) {',
  '    Site s = <span class="k">listen</span>(client);',
  '    s.layout  = <span class="s">"clean"</span>;',
  '    s.mobile  = <span class="s">true</span>;',
  '    s.speed   = <span class="s">FAST</span>;',
  '    <span class="k">return</span> <span class="k">launch</span>(s);  <span class="c">// 0 = success</span>',
  '}'
];
const code = document.getElementById('code');
const html = lines.join('\n');
if (matchMedia('(prefers-reduced-motion: reduce)').matches) {
  code.innerHTML = html;
} else {
  // type character by character, but insert whole tags at once
  let i = 0, out = '';
  (function tick() {
    if (i >= html.length) return;
    if (html[i] === '<') i = html.indexOf('>', i) + 1; else i++;
    code.innerHTML = html.slice(0, i);
    setTimeout(tick, 14);
  })();
}

// Contact form: validates, then opens the visitor's email app
// CHANGE THIS to your own email address
const MY_EMAIL = 'you@example.com';
const form = document.getElementById('form'), status = document.getElementById('status');
form.addEventListener('submit', e => {
  e.preventDefault();
  let ok = true;
  form.querySelectorAll('[required]').forEach(f => {
    const bad = !f.value.trim() || (f.type === 'email' && !/^\S+@\S+\.\S+$/.test(f.value));
    f.classList.toggle('bad', bad); if (bad) ok = false;
  });
  status.className = ok ? '' : 'err';
  if (!ok) { status.textContent = 'Please fill in your name, a valid email and a message.'; return; }
  const d = new FormData(form);
  location.href = `mailto:${MY_EMAIL}?subject=${encodeURIComponent('Project enquiry from ' + d.get('name'))}&body=${encodeURIComponent(d.get('msg') + '\n\nReply to: ' + d.get('email'))}`;
  status.textContent = 'Opening your email app. If nothing opens, write to ' + MY_EMAIL + '.';
});

document.getElementById('yr').textContent = new Date().getFullYear();
