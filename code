struct fraction{
	using ll = long long;

	bool neg;	//if fraction < 0 then neg = true
	ll a, b;	//a for numerator, b for denominator

	static ll mygcd(ll x, ll y){
		if(!y) return x;
		return mygcd(y, x % y);
	}
	static ll mylcm(ll x, ll y){
		return x * (y / mygcd(x, y));
	}

	fraction(ll _a = 0) : a(abs(_a)), b(1), neg(_a < 0) {}
	fraction(ll _a, ll _b) : a(abs(_a)), b(abs(_b)), neg((_a < 0 && _b > 0) || (_a > 0 && _b < 0)) {
		if(!b) {
			cout << "0";
			throw "cannot divide by 0";
		}
		ll k = mygcd(a, b);
		a /= k, b /= k;
	}
	fraction(ll _a, ll _b, bool _neg) : a(abs(_a)), b(abs(_b)), neg(_neg) {
		if(!b) {
			cout << "0";
			throw "cannot divide by 0";
		}
		if(_a < 0 || _b < 0 || (!_a && _neg)) {
			if(_a < 0)cout << "A";
			else if( _b < 0)cout << "B";
			else cout << "NEG";
			cout << "\ninit\n";
			throw "invalid initialization";
		}
		ll k = mygcd(a, b);
		a /= k, b /= k;
	}

	bool operator!() { return !a; }
	fraction operator+(fraction t){
		ll c = mylcm(b, t.b);
		if(!neg && !t.neg) return fraction(a * (c / b) + t.a * (c / t.b), c);
		else if(!neg && t.neg) return fraction(a * (c / b) - t.a * (c / t.b), c);
		else if(neg && !t.neg) return t + (*this);
		else return fraction(a * (c / b) + t.a * (c / t.b), c, true);
	}
	fraction operator-(fraction t){
		if(!!t) t.neg = !t.neg;
		return (*this) + t;
	}
	fraction operator*(fraction t){
		if(!(*this) || !t) return fraction(0);
		ll c = mygcd(a, t.b), d = mygcd(b, t.a);
		return fraction((a / c) * (t.a / d), (b / d) * (t.b / c), neg != t.neg);
	}
	fraction operator/(fraction t){
		return (*this) * fraction(t.b, t.a);
	}
	fraction operator-(){
		fraction t(*this);
		if(!!t) t.neg = !t.neg;
		return t;
	}
	bool operator==(fraction t){ return (a == t.a && b == t.b && neg == t.neg); }
	bool operator!=(fraction t){ return !((*this) == t); }
	bool operator>=(fraction t){ return ((*this) - t).neg; }
	bool operator>(fraction t){ return (((*this) != t) && ((*this) >= t)); }
	bool operator<=(fraction t){ return !((*this) > t); }
	bool operator<(fraction t){ return !((*this) >= t); }
};
