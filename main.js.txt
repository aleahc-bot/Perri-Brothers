/* asset paths, generated at build time */
var IMG={
  "living": "images/project-fireplace-builtins.webp",
  "kitchen": "images/project-kitchen-navy-island.webp",
  "bath": "images/project-bath-travertine.webp",
  "team": "images/team-perri-brothers.webp",
  "k_pend": "images/detail-brass-pendants.webp",
  "k_isle": "images/detail-navy-cabinetry.webp",
  "b_tub": "images/detail-freestanding-tub.webp",
  "b_van": "images/detail-vanity-sconces.webp",
  "l_fire": "images/detail-marble-fireplace.webp",
  "l_shelf": "images/detail-builtin-shelving.webp",
  "bath1_b": "images/beforeafter-guest-bath-before.webp",
  "bath1_a": "images/beforeafter-guest-bath-after.webp",
  "foyer_b": "images/beforeafter-foyer-ceiling-before.webp",
  "foyer_a": "images/beforeafter-foyer-ceiling-after.webp",
  "kitch_b": "images/beforeafter-kitchen-ceiling-before.webp",
  "kitch_a": "images/beforeafter-kitchen-ceiling-after.webp",
  "showr_b": "images/beforeafter-shower-before.webp",
  "showr_a": "images/beforeafter-shower-after.webp",
  "vanit_b": "images/beforeafter-primary-bath-before.webp",
  "vanit_a": "images/beforeafter-primary-bath-after.webp",
  "svc_reno": "images/service-full-renovations.webp",
  "svc_bath": "images/service-kitchen-and-bath.webp",
  "svc_carp": "images/service-custom-carpentry.webp",
  "svc_env": "images/service-siding-windows-doors.webp",
  "rev_a": "images/work-walk-in-shower.webp",
  "rev_b": "images/work-guest-bath.webp",
  "pbmark": "images/logo-monogram-framed.png",
  "hero_a": "images/hero-interior-entry.webp",
  "hero_b": "images/hero-detail-fireplace.webp"
};
var LOGO={word:"images/logo-wordmark.png"};

(function(){
  var RM=matchMedia('(prefers-reduced-motion: reduce)').matches;

  ['navLogo','ftLogo','banLogo'].forEach(function(id){var e=document.getElementById(id);if(e)e.src=LOGO.word});

  function hydrate(){
    document.querySelectorAll('[data-img]').forEach(function(e){
      if(e.getAttribute('src'))return;
      var s=IMG[e.getAttribute('data-img')];
      if(!s)return;
      /* the hero paints straight away; everything below the fold defers */
      if(!e.closest('.hero')){ e.loading='lazy'; e.decoding='async'; }
      e.src=s;
    });
  }

  /* card    = short description on the home page service cards
     teaser  = one-line description in the services page accordion header
     p       = main paragraph inside the open accordion panel
     s       = scope list, f = "right call if" line */
  var SVC=[
    {n:'01',t:'Full-Service Renovations',img:'svc_reno',det:'l_fire',
     card:'Complete home, condominium, and commercial renovations designed around your goals, budget, and timeline\u2014from structural updates to the finishing touches.',
     teaser:'Complete home, condominium, and commercial renovations, managed from planning and permitting through the final details.',
     p:'Complete home, condominium, and commercial renovations designed around your goals, budget, and timeline\u2014from structural updates to the finishing touches.',
     tags:['Structural Improvements','Layout Changes','Interior Finishes','Permitting'],
     s:['Demolition & Haul-Off','Structural & Layout Changes','Electrical & Plumbing Coordination','Drywall, Paint & Trim','Flooring & Tile','Final Punch & Walkthrough'],
     f:'You are changing how the space works, not just how it looks.'},
    {n:'02',t:'Kitchen & Bathroom Remodeling',img:'svc_bath',det:'b_tub',
     card:'Transform the two most important rooms in your home with thoughtful design, quality materials, and expert craftsmanship built to last.',
     teaser:'The spaces you use every day deserve thoughtful design and lasting craftsmanship.',
     p:'Your kitchen and bathrooms should be as functional as they are beautiful. We design each space around how you live, then select quality materials and finishes that perform in Southwest Florida\u2019s climate.',
     tags:['Quartz Countertops','Travertine','Custom Cabinetry'],
     s:['Quartz & Stone Countertops','Travertine, Tile & Stone Flooring','Under-Cabinet Lighting','Custom & Semi-Custom Cabinetry','Freestanding & Built-In Tubs','Fixture & Hardware Selection'],
     f:'Your layout still works, but outdated finishes are keeping your home from reaching its full potential.'},
    {n:'03',t:'Custom Carpentry & Cabinetry',img:'living',det:'k_isle',
     card:'Custom-built woodwork and cabinetry designed to maximize beauty, functionality, and storage throughout your home.',
     teaser:'Custom-built woodwork and cabinetry designed to fit your home, your style, and your space.',
     p:'Custom-built woodwork and cabinetry designed to maximize beauty, functionality, and storage throughout your home.',
     tags:['Built-Ins','Millwork','Soft-Close Hardware'],
     s:['Built-In Shelving & Storage','Mantels & Feature Walls','Shaker & Flat-Panel Doors','Soft-Close Hardware','Crown, Base & Casing','Closet & Pantry Systems'],
     f:'Stock cabinetry will not fit the wall you actually have.'},
    {n:'04',t:'Siding, Windows & Doors',img:'svc_env',det:'bath',
     card:'Protect and enhance your home\u2019s exterior with durable products designed to perform in Southwest Florida\u2019s demanding climate.',
     teaser:'Protect your home with high-performance exterior products designed for Southwest Florida\u2019s climate and storm seasons.',
     p:'Protect and enhance your home\u2019s exterior with durable products designed to perform in Southwest Florida\u2019s demanding climate.',
     tags:['Impact Windows','Flashing','Siding Systems'],
     s:['Impact-Rated Windows','Entry & Slider Replacement','Siding Repair & Replacement','Flashing & Waterproofing','Soffit & Fascia','Post-Storm Exterior Repair'],
     f:'Your openings predate current wind codes, or you are chasing a leak.'},
    {n:'05',t:'New Construction',img:'svc_carp',det:'living',
     card:'From concept to completion, we build custom residential and commercial spaces with meticulous attention to quality, craftsmanship, and code compliance.',
     teaser:'Custom residential and commercial construction built with quality craftsmanship from the ground up.',
     p:'From concept to completion, we build custom residential and commercial spaces with meticulous attention to quality, craftsmanship, and code compliance.',
     tags:['Permitting','Structural Framing','Florida Building Code'],
     s:['Permitting & Approvals','Site Work & Foundations','Framing & Dry-In','Wind & Elevation Compliance','Full Interior Finish','Certificate of Occupancy'],
     f:'You are building on a lot, or a rebuild is cheaper than the repair.'}
  ];

  /* home: service cards */
  var sc=document.getElementById('svcCards');
  if(sc) sc.innerHTML=SVC.map(function(s,i){
    return '<a class="card sp4" href="#/services" data-go="services" data-r style="--d:'+(i%3*70)+'ms">'+
      '<span class="card__i"><img data-img="'+s.img+'" alt="'+s.t+'"></span>'+
      '<span class="card__b"><span class="lbl">Service '+s.n+'</span>'+
      '<h3 class="s3" style="margin-top:7px">'+s.t+'</h3>'+
      '<p class="p">'+s.card+'</p>'+
      '<span class="tags">'+s.tags.map(function(t){return '<span>'+t+'</span>'}).join('')+'</span></span></a>';
  }).join('')+
    '<div class="card card--d sp4" data-r style="--d:140ms">'+
      '<div><span class="lbl">Not sure where to start?</span>'+
      '<h3 class="s3" style="margin-top:8px;color:var(--cream)">Tell us your vision. We\u2019ll help you build it.</h3>'+
      '<p class="p" style="margin-top:8px">Whether you\u2019re planning a renovation, recovering from storm damage, or starting new construction, we\u2019ll help you determine the right solution and guide you through the next steps.</p></div>'+
      '<a class="b b--od b--s" style="margin-top:18px;align-self:flex-start" href="#/contact" data-go="contact">Book a walkthrough</a></div>';

  /* services page: full detail */
  var sf=document.getElementById('svcFull');
  if(sf){
    sf.className='acc';
    sf.innerHTML=SVC.map(function(s,i){
      return '<div class="acc__i'+(i===0?' open':'')+'">'+
        '<button class="acc__h" aria-expanded="'+(i===0?'true':'false')+'" aria-controls="acc-p'+i+'">'+
          '<span class="acc__n">'+s.n+'</span>'+
          '<span class="acc__t"><span class="acc__title">'+s.t+'</span>'+
            '<span class="acc__sub">'+s.tags.join(' &middot; ')+'</span></span>'+
          '<span class="acc__teaser">'+s.teaser+'</span>'+
          '<span class="acc__ic" aria-hidden="true"><i></i><i></i></span>'+
        '</button>'+
        '<div class="acc__p" id="acc-p'+i+'" role="region">'+
          '<div class="acc__in">'+
            '<div><p class="p">'+s.p+'</p>'+
              '<div class="acc__scope">'+s.s.map(function(x){return '<div>'+x+'</div>'}).join('')+'</div>'+
              '<p class="acc__fit"><b>Right call if</b>'+s.f+'</p>'+
            '</div>'+
            '<div class="acc__m"><img data-img="'+s.img+'" alt="'+s.t+'"></div>'+
          '</div>'+
        '</div></div>';
    }).join('');

    var items=[].slice.call(sf.querySelectorAll('.acc__i'));
    function panel(it){return it.querySelector('.acc__p')}
    function setOpen(it,open){
      it.classList.toggle('open',open);
      it.querySelector('.acc__h').setAttribute('aria-expanded',open?'true':'false');
      var p=panel(it);
      p.style.maxHeight = open ? p.scrollHeight+'px' : '0px';
    }
    items.forEach(function(it){
      it.querySelector('.acc__h').addEventListener('click',function(){
        var isOpen=it.classList.contains('open');
        items.forEach(function(o){ if(o!==it) setOpen(o,false); });
        setOpen(it,!isOpen);
      });
    });
    /* first panel starts open; measure after images and fonts settle */
    function remeasure(){
      items.forEach(function(it){ if(it.classList.contains('open')){ panel(it).style.maxHeight=panel(it).scrollHeight+'px'; } });
    }
    setOpen(items[0],true);
    addEventListener('resize',remeasure);
    addEventListener('load',remeasure);
    setTimeout(remeasure,300);
    sf.querySelectorAll('img').forEach(function(im){im.addEventListener('load',remeasure)});
  }

  var REV=[
    ['Mark Butler','Storm repair, Fort Myers Beach, FL','My home in Fort Myers Beach had considerable damage from Hurricane Milton: roof damage, leakage, drywall, and siding that needed handling fast so it would not get worse. Perri Brothers came and checked out my situation and gave me an estimate. They jumped right on it, stopped my roof leakage, and repaired my deck and siding. They did a great job, did it in a timely fashion, and I thought they were very reasonably priced. If anything else comes up, I will reach out to them first.'],
    ['Karen and Michael DeLuca','Kitchen remodel, Naples, FL','We hired this family team to completely remodel our outdated Naples kitchen, and the result is beyond anything we imagined. They opened up the space, added a massive quartz waterfall island, and tied in coastal-modern finishes that feel right at home here. Their attention to detail, from the cabinet lighting to the soft-close custom drawers, is next-level. It is now the centerpiece of our home and the first thing guests rave about.'],
    ['Bryan Schultz','Full rebuild, Estero, FL','After Hurricane Ian we needed a renovation team we could trust, and this family-owned crew treated us like one of their own. They rebuilt our interior walls, installed new LVP flooring throughout, redesigned our kitchen, and helped us choose materials that can handle Florida storms and humidity. They coordinated everything flawlessly and turned a stressful situation into a fresh start.'],
    ['Renee Alvarez','Bathroom remodel, Fort Myers, FL','Our master bathroom in Fort Myers desperately needed a refresh, and this company delivered a true spa retreat. They installed a walk-in shower with floor-to-ceiling tile, a freestanding tub, and added hurricane-rated windows that brighten the whole suite. Their craftsmanship is phenomenal, and they handled every detail with care. We finally have the sanctuary we always wanted.'],
    ['Tom and Jessica Harrington','Outdoor living, Cape Coral, FL','We wanted a lanai that would let us enjoy the Cape Coral sunsets without battling mosquitoes, and they absolutely nailed it. The new panoramic screen enclosure gives us an unobstructed view of the canal, and the travertine flooring they suggested stays cool even on hot afternoons. It is now our favorite space in the house: morning coffee, evening wine, everything happens out there.']
  ];
  function short(t){var p=t.split('. ');return p.slice(0,2).join('. ')+'.';}
  var tc=document.getElementById('tstCards');
  if(tc) tc.innerHTML=REV.slice(0,3).map(function(r,i){
    return '<figure class="tst sp4" data-r style="--d:'+(i*70)+'ms">'+
      '<div class="st">★★★★★</div><blockquote>"'+short(r[2])+'"</blockquote>'+
      '<figcaption>'+r[0]+'<em>'+r[1]+'</em></figcaption></figure>';
  }).join('');
  var rf=document.getElementById('revFull');
  if(rf) rf.innerHTML=REV.map(function(r,i){
    return '<figure class="rvrow" data-r style="--d:'+(i%3*60)+'ms">'+
      '<div class="rvrow__m"><div class="st">★★★★★</div><b>'+r[0]+'</b><span>'+r[1]+'</span></div>'+
      '<blockquote class="rvrow__q">"'+r[2]+'"</blockquote></figure>';
  }).join('');

  hydrate();
  document.documentElement.classList.add('js');

  var io=new IntersectionObserver(function(es){
    es.forEach(function(e){if(e.isIntersecting){e.target.classList.add('in');io.unobserve(e.target)}})
  },{threshold:.04,rootMargin:'0px 0px -3% 0px'});
  function watch(s){(s||document).querySelectorAll('[data-r]:not(.in)').forEach(function(e){io.observe(e)})}
  function revealAll(){document.querySelectorAll('[data-r]:not(.in)').forEach(function(e){e.classList.add('in')})}
  setTimeout(revealAll,1400);
  addEventListener('load',function(){setTimeout(revealAll,400)});

  var P=['home','about','services','process','reviews','contact'];
  function paint(id){
    if(P.indexOf(id)<0)id='home';
    document.querySelectorAll('.page').forEach(function(p){p.classList.toggle('on',p.id==='p-'+id)});
    document.querySelectorAll('#links a').forEach(function(a){a.classList.toggle('on',a.getAttribute('data-go')===id)});
    scrollTo(0,0);
    var pg=document.getElementById('p-'+id);
    pg.querySelectorAll('[data-r]').forEach(function(e){e.classList.remove('in')});
    watch(pg);
    setTimeout(function(){rowSyncs.forEach(function(f){f()})},60);
    setTimeout(revealAll,1400);
  }
  document.addEventListener('click',function(e){
    var a=e.target.closest('[data-go]');if(!a)return;
    e.preventDefault();
    var id=a.getAttribute('data-go');
    /* keep the query string, otherwise ?preview is dropped on the first nav click */
    if(!PREVIEW&&location.hash!=='#/'+id){try{history.pushState(null,'',location.search+'#/'+id)}catch(err){}}
    document.body.classList.remove('mo');
    paint(id);
  });
  addEventListener('popstate',function(){paint((location.hash||'#/home').replace('#/','')||'home')});
  document.getElementById('bg').addEventListener('click',function(){document.body.classList.toggle('mo')});

  var nav=document.getElementById('nav');
  function st(){nav.classList.toggle('stk',scrollY>10)}
  st();addEventListener('scroll',st,{passive:true});

  var cio=new IntersectionObserver(function(es){
    es.forEach(function(e){
      if(!e.isIntersecting)return;
      var el=e.target,end=parseInt(el.getAttribute('data-count'),10),t0=null;
      if(RM||isNaN(end)){cio.unobserve(el);return}
      requestAnimationFrame(function tick(t){
        if(!t0)t0=t;var p=Math.min((t-t0)/850,1);
        el.textContent=Math.round(end*(1-Math.pow(1-p,3)));
        if(p<1)requestAnimationFrame(tick);
      });
      cio.unobserve(el);
    })
  },{threshold:.5});
  document.querySelectorAll('[data-count]').forEach(function(e){cio.observe(e)});

  /* ---------- contact form ----------
     The contact form is a LeadConnector (HighLevel) embed, added directly to
     index.html as an iframe. Submissions go straight into the CRM, so there is no
     handler here. Field labels, placeholders, the submit button and the thank-you
     message are all edited in the LeadConnector form builder, not in this file.
     If the embed is ever swapped back out for a native form, the previous version
     of this block is in git history. */

  /* ---------- before / after carousel ---------- */
  var BA=[
    ['bath1','Guest Bathroom Remodel','Fort Myers','This narrow guest bathroom was completely transformed with a full renovation, featuring a custom tub surround, large-format porcelain tile, quartz countertops, and a dark shaker vanity. Existing architectural details were preserved where possible to create a space that feels both modern and timeless.',['Demo to Studs','Tub Surround','Quartz Countertops','Custom Vanity']],
    ['foyer','Custom Entry Foyer Ceiling','Southwest Florida','To restore and enhance this home\u2019s entryway, we rebuilt the ceiling from the framing up, installed new wiring and ductwork, and finished it with stained tongue-and-groove pine, custom trim, and updated lighting. The result is a warm, inviting entrance built to last.',['Ceiling Rebuild','Tongue & Groove Pine','Custom Trim','New Wiring']],
    ['kitch','Kitchen Ceiling','Cape Coral','Ceiling opened up for insulation and electrical, then closed with a plank tray, crown, and concealed LED cove lighting on a color changer.',['Tray Ceiling','Cove Lighting','Insulation','Crown Molding']],
    ['showr','Walk-In Shower','Southwest Florida','Dated square tile and a failing pan replaced with a full-height grey subway surround, penny-round floor, matte black fittings and a frameless glass panel.',['New Shower Pan','Subway Tile','Penny Round Floor','Matte Black Fittings']],
    ['vanit','Primary Bathroom','Southwest Florida','Stripped back to bare walls and rebuilt with a double vanity, large-format grey tile, black fixtures and framed mirrors.',['Double Vanity','Large-Format Tile','Framed Mirrors','Black Fixtures']]
  ];
  var baTrack=document.getElementById('baTrack');
  if(baTrack){
    baTrack.innerHTML=BA.map(function(p,i){
      return '<div class="ba__slide">'+
        '<div class="cmp">'+
          '<img data-img="'+p[0]+'_a" alt="'+p[1]+' after renovation">'+
          '<div class="cmp__b"><img data-img="'+p[0]+'_b" alt="'+p[1]+' before renovation"></div>'+
          '<span class="cmp__tag cmp__tag--b">Before</span>'+
          '<span class="cmp__tag cmp__tag--a">After</span>'+
          '<button class="cmp__h" role="slider" aria-label="Compare before and after" aria-valuemin="0" aria-valuemax="100" aria-valuenow="50"><span class="cmp__ar">&#8596;</span></button>'+
        '</div>'+
        '<div class="ba__meta">'+
          '<span class="lbl">Project 0'+(i+1)+' &middot; '+p[2]+'</span>'+
          '<h3 class="s3" style="margin-top:6px">'+p[1]+'</h3>'+
          '<p class="p" style="margin-top:10px">'+p[3]+'</p>'+
          '<div class="ba__chips">'+p[4].map(function(c){return '<span>'+c+'</span>'}).join('')+'</div>'+
        '</div></div>';
    }).join('');

    document.querySelectorAll('.cmp').forEach(function(el){
      var before=el.querySelector('.cmp__b'), handle=el.querySelector('.cmp__h'), p=50, drag=false;
      function set(v){
        p=Math.max(0,Math.min(100,v));
        before.style.clipPath='inset(0 '+(100-p)+'% 0 0)';
        handle.style.left=p+'%';
        handle.setAttribute('aria-valuenow',Math.round(p));
      }
      function fromX(x){var r=el.getBoundingClientRect();set((x-r.left)/r.width*100)}
      el.addEventListener('pointerdown',function(e){
        /* on touch only the handle starts a wipe, so a swipe across the photo still moves the carousel */
        if(e.pointerType==='touch' && !e.target.closest('.cmp__h')) return;
        drag=true;
        try{el.setPointerCapture(e.pointerId)}catch(err){}
        fromX(e.clientX); e.preventDefault();
      });
      el.addEventListener('pointermove',function(e){if(drag){fromX(e.clientX);e.preventDefault()}});
      ['pointerup','pointercancel','pointerleave'].forEach(function(ev){
        el.addEventListener(ev,function(){drag=false});
      });
      handle.addEventListener('keydown',function(e){
        if(e.key==='ArrowLeft'){set(p-4);e.preventDefault()}
        if(e.key==='ArrowRight'){set(p+4);e.preventDefault()}
        if(e.key==='Home'){set(0);e.preventDefault()}
        if(e.key==='End'){set(100);e.preventDefault()}
      });
      set(50);
    });

    hydrate();   /* carousel is built after the first hydrate pass, so fill its images now */

    var dots=document.getElementById('baDots');
    dots.innerHTML=BA.map(function(_,i){return '<i'+(i===0?' class="on"':'')+'></i>'}).join('');
    function step(){
      var s=baTrack.querySelector('.ba__slide');
      if(!s) return baTrack.clientWidth;
      var g=parseFloat(getComputedStyle(baTrack).columnGap||getComputedStyle(baTrack).gap)||0;
      return s.getBoundingClientRect().width+g;
    }
    function idx(){return Math.round(baTrack.scrollLeft/Math.max(1,step()))}
    function go(n){
      n=Math.max(0,Math.min(BA.length-1,n));
      baTrack.scrollTo({left:n*step(),behavior:'smooth'});
    }
    document.getElementById('baPrev').addEventListener('click',function(){go(idx()-1)});
    document.getElementById('baNext').addEventListener('click',function(){go(idx()+1)});
    var tick;
    baTrack.addEventListener('scroll',function(){
      clearTimeout(tick);
      tick=setTimeout(function(){
        var n=idx();
        [].forEach.call(dots.children,function(d,i){d.classList.toggle('on',i===n)});
      },60);
    },{passive:true});
  }


  /* ---------- device preview ----------
     Hidden from visitors. Add ?preview to the url to switch it on, e.g.
     https://perribrothers.com/?preview
     Inside the preview iframe the flag is data-preview, which hides the controls
     so you never get a preview inside a preview. */
  var PREVIEW=document.documentElement.hasAttribute('data-preview');
  /* The tester switches itself on when you are working locally (opening the file directly,
     or a dev server), and on a public url only when you ask for it with ?preview.
     Because this is a hash-routed site the flag can land inside the hash, so the whole url
     is checked, and once seen it is remembered for the tab so navigation cannot lose it. */
  var _flag=/[?&#]preview\b/.test(location.href);
  try{ if(_flag) sessionStorage.setItem('pbPreview','1'); }catch(e){}
  var _saved=false; try{ _saved=sessionStorage.getItem('pbPreview')==='1'; }catch(e){}
  var _local = location.protocol==='file:' || location.hostname==='' ||
               /^(localhost|127\.|0\.0\.0\.0|192\.168\.|10\.)/.test(location.hostname);
  var PREVIEW_ON = !PREVIEW && (_local || _flag || _saved);
  var fabEl=document.getElementById('fab');
  if(fabEl && !PREVIEW_ON){ fabEl.remove(); var w=document.getElementById('dvw'); if(w)w.remove();
    var b=document.getElementById('dvbar'); if(b)b.remove(); }
  /* external css/js need an absolute base once the markup is copied into srcdoc */
  var SNAP='<head><base href="'+location.href.split(/[?#]/)[0]+'">'+document.head.innerHTML+
           '</head><body>'+document.body.innerHTML+'</body>';

  /* ---------- floating device preview ---------- */
  if(PREVIEW_ON){
    var DEVICES={
      mobile:[['iPhone SE',375,667],['iPhone 13 mini',375,812],['iPhone 14 / 15',390,844],
              ['iPhone 15 Pro Max',430,932],['Pixel 8',412,915],['Galaxy S23',360,780]],
      tablet:[['iPad mini',744,1133],['iPad 10.9',820,1180],['iPad Pro 11',834,1194],
              ['iPad Pro 12.9',1024,1366],['Galaxy Tab S9',800,1280]],
      desktop:[['Laptop 1280',1280,800],['Laptop 1440',1440,900],
               ['Desktop 1680',1680,1050],['Full HD 1920',1920,1080]]
    };
    var DEFAULTS={mobile:2,tablet:2,desktop:1};
    var fab=document.getElementById('fab'),fabB=document.getElementById('fabB'),
        dvw=document.getElementById('dvw'),dvf=document.getElementById('dvframe'),
        dvbar=document.getElementById('dvbar'),dvSel=document.getElementById('dvSel'),
        dvRot=document.getElementById('dvRot'),dvi=document.getElementById('dvif'),
        dvl=document.getElementById('dvlabel'),
        cur=null,rot=false,scrollLock=0;

    Object.keys(DEVICES).forEach(function(cat){
      var g=document.createElement('optgroup');
      g.label=cat.charAt(0).toUpperCase()+cat.slice(1);
      DEVICES[cat].forEach(function(d,n){
        var o=document.createElement('option');
        o.value=cat+':'+n; o.textContent=d[0]+'  '+d[1]+'x'+d[2];
        g.appendChild(o);
      });
      dvSel.appendChild(g);
    });

    function open_(v){
      document.body.classList.toggle('fab-open',v);
      fabB.setAttribute('aria-expanded',v?'true':'false');
    }
    fabB.addEventListener('click',function(){open_(!document.body.classList.contains('fab-open'))});

    function dims(){
      var p=cur.split(':'),d=DEVICES[p[0]][+p[1]];
      return rot?[d[2],d[1]]:[d[1],d[2]];
    }
    function fit(){
      if(!cur)return;
      var d=dims(),aw=innerWidth-40,ah=innerHeight-150;
      var s=Math.min(1,aw/(d[0]+24),ah/(d[1]+24));
      dvf.style.transform='scale('+s+')';
      dvf.style.marginBottom=(d[1]+24)*(s-1)+'px';
    }
    function render(){
      var d=dims();
      dvi.style.width=d[0]+'px';dvi.style.height=d[1]+'px';
      dvf.style.width=(d[0]+24)+'px';dvf.style.height=(d[1]+24)+'px';
      dvl.textContent=d[0]+' \u00d7 '+d[1];
      dvSel.value=cur;
      fit();
    }
    function show(key){
      cur=key;
      if(!dvi.getAttribute('srcdoc'))
        dvi.setAttribute('srcdoc','<!DOCTYPE html><html lang="en" data-preview="1">'+SNAP+'</html>');
      if(!dvw.classList.contains('on')){
        scrollLock=scrollY;
        document.body.style.top=(-scrollLock)+'px';
        document.body.classList.add('dv-lock');
      }
      dvw.classList.add('on');document.body.classList.add('dv-on');
      render();
    }
    function hide(){
      if(!cur)return;
      cur=null;rot=false;
      dvw.classList.remove('on');
      document.body.classList.remove('dv-on','dv-lock');
      document.body.style.top='';
      window.scrollTo(0,scrollLock);
      dvl.textContent='';
      fab.querySelectorAll('.fab__o').forEach(function(x){x.classList.toggle('on',x.getAttribute('data-dev')==='live')});
    }
    document.getElementById('fabM').addEventListener('click',function(e){
      var b=e.target.closest('button[data-dev]');if(!b)return;
      fab.querySelectorAll('.fab__o').forEach(function(x){x.classList.toggle('on',x===b)});
      var dev=b.getAttribute('data-dev');
      if(dev==='live'){hide();open_(false);}
      else{rot=false;show(dev+':'+DEFAULTS[dev]);}
    });
    dvSel.addEventListener('change',function(){rot=false;show(dvSel.value)});
    dvRot.addEventListener('click',function(){if(!cur)return;rot=!rot;render()});
    document.getElementById('dvClose').addEventListener('click',function(){hide();open_(false)});
    addEventListener('resize',fit);
    addEventListener('keydown',function(e){
      if(e.key!=='Escape')return;
      hide();open_(false);
    });
  }

  /* Shift + D toggles the tester on, in case the query string ever gets lost */
  addEventListener('keydown',function(e){
    if(!e.shiftKey||String(e.key).toLowerCase()!=='d'||PREVIEW)return;
    var t=e.target&&e.target.tagName;
    if(t==='INPUT'||t==='TEXTAREA'||t==='SELECT')return;
    try{sessionStorage.setItem('pbPreview','1')}catch(err){}
    location.reload();
  });

  /* ---------- swipe rows: arrows + mouse drag ----------
     overflow-x:auto is untouchable with a mouse once the scrollbar is hidden,
     so each row also gets buttons and click-drag scrolling. */
  var rowSyncs=[];
  function initRow(row){
    if(!row||row.dataset.rowInit)return;
    row.dataset.rowInit='1';
    var bar=document.createElement('div');bar.className='srow';
    var prev=document.createElement('button');prev.className='srow__b';prev.type='button';
    prev.setAttribute('aria-label','Previous');prev.innerHTML='&larr;';
    var next=document.createElement('button');next.className='srow__b';next.type='button';
    next.setAttribute('aria-label','Next');next.innerHTML='&rarr;';
    var tip=document.createElement('span');tip.className='srow__t';tip.textContent='Swipe or use the arrows';
    bar.appendChild(prev);bar.appendChild(next);bar.appendChild(tip);
    row.parentNode.insertBefore(bar,row.nextSibling);
    function stepSize(){
      var c=row.firstElementChild;if(!c)return row.clientWidth;
      var g=parseFloat(getComputedStyle(row).columnGap||getComputedStyle(row).gap)||0;
      return c.getBoundingClientRect().width+g;
    }
    function sync(){
      var max=row.scrollWidth-row.clientWidth-2;
      bar.style.display=max>4?'flex':'none';
      prev.disabled=row.scrollLeft<=2;
      next.disabled=row.scrollLeft>=max;
    }
    prev.addEventListener('click',function(){row.scrollBy({left:-stepSize(),behavior:'smooth'})});
    next.addEventListener('click',function(){row.scrollBy({left:stepSize(),behavior:'smooth'})});
    rowSyncs.push(sync);
    row.addEventListener('scroll',sync,{passive:true});
    addEventListener('resize',sync);
    addEventListener('load',sync);
    setTimeout(sync,150);
    var down=false,sx=0,sl=0,moved=0;
    row.addEventListener('pointerdown',function(e){
      if(e.pointerType==='touch')return;
      down=true;moved=0;sx=e.clientX;sl=row.scrollLeft;
    });
    row.addEventListener('pointermove',function(e){
      if(!down)return;
      var d=e.clientX-sx;moved=Math.abs(d);
      if(moved>4)row.classList.add('dragging');
      row.scrollLeft=sl-d;e.preventDefault();
    });
    ['pointerup','pointercancel','pointerleave'].forEach(function(ev){
      row.addEventListener(ev,function(){down=false;row.classList.remove('dragging')});
    });
    row.addEventListener('click',function(e){if(moved>6){e.preventDefault();e.stopPropagation();}},true);
  }
  ['#svcCards','#tstCards','#valGrid','#honestGrid','.tl'].forEach(function(sel){
    document.querySelectorAll(sel).forEach(initRow);
  });

  watch(document);
  paint((location.hash||'#/home').replace('#/','')||'home');
})();
